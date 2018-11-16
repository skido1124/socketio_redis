# websocket + redis の pub/sub テスト

## 前準備
`npm install`, redis のインストールをしておく

```
# redis 起動。6379ポート
$ redis-server

# 起動
$ node app

# localhost:7000 で表示
```

## 動作フロー

1. localhost:7000 のフォームから send
2. websocket で送信された値が redis で publish
3. subscrbe していた値を emit
4. localhost:7000 で websocket で受け取って表示

## redis-cli から操作

```
$ redis-cli

# SUBSCRIBE {channel}
$ 127.0.0.1:6379 > SUBSCLIBE test

# PUBLISH {channel} {message}
$ 127.0.0.1:6379 > PUBLISH test "test message"
$ (integer) 1  # 1 は成功
```
