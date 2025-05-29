```
writefasta([io::IO = stdout], data; check_description=true)
```

このバージョンの関数は、すでに開かれている `IO` ストリームに書き込み、デフォルトは `stdout` です。

キーワード `check_description=false` を設定すると、説明行が長すぎるときに表示される警告メッセージを無効にします。
