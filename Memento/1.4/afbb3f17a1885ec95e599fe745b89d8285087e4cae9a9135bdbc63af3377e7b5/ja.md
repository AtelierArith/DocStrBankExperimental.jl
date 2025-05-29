```
emit{F, O}(handler::DefaultHandler{F ,O}, rec::Record) where {F<:Formatter, O<:IO}
```

任意の `Formatter` と `IO` タイプを使用して、任意の `Record` の印刷を処理します。
