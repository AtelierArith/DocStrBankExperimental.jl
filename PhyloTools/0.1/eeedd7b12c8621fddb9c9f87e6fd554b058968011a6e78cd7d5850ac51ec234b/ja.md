```
writenw(io::IO, n)
writenw(fname::AbstractString, n)
```

`n`に根ざした木のNewick表現を書きます。木のデータ型は`nwstr(n)`が機能することを許可する必要があります。`nwstr`のドキュメント文字列を参照してください。
