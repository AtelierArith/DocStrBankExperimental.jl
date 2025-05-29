```
query(rp::RedPitaya, cmd, T::Type [timeout = 5.0, N = 100])
```

RedPitayaにクエリを送信します。返信を`T`として解析します。

`timeout`秒待機し、`timeout/N`秒ごとにチェックします。
