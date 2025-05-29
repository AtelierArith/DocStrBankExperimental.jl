```
send(lk::Link, msg...)
send(name::Symbol, msg...)
```

アクター `lk`（または登録された `name`）にメッセージを送信します。 `msg...` はアクターの動作関数への通信パラメータです。
