```
NamedTupleArg(; key::Symbol, value=not_provided, is_splat::Bool=false, kw_head::Bool)

NamedTupleArg(key::Symbol; kw_head::Bool)
```

`NamedTuple`式の中で`key = value`または`key`引数に一致します。

`kw_head == true`の場合、式の先頭は`:kw`に設定され、それ以外の場合は`:(=)`になります。
