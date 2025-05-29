```
LogRecordData(data)

LogRecordData(args::Pair{<:Any, <:Any}...)
```

ログレコードに添付されたオプションの `key => value` ペアのコレクションを表す型です。

`data` は、各要素が `Pair` である反復可能なコレクションでなければなりません。
