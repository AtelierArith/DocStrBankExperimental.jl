```
writemessage(handle::Message, filename::AbstractString; mode="wb")
```

`handle`で表されるメッセージを`filename`のファイルに書き込みます。

`mode`は`Base.open`で説明されているモードです。
