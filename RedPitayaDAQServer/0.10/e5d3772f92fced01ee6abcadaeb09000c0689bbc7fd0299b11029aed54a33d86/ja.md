```
query(rp::RedPitaya, cmd [, timeout = 5.0, N = 100])
```

RedPitayaコマンドソケットにクエリを送信します。返信をStringとして返します。

`timeout`秒待機し、毎`timeout/N`秒ごとにチェックします。

詳細は[receive](@ref)を参照してください。
