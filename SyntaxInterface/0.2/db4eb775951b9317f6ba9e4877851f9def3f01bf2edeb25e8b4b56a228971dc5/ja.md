```
similarterm(x::T, head, args)
```

型 `T` の同じクロージャのノードにある項を返し、`head` をヘッド、`args` を引数として使用します。デフォルトでは `head(args...)` が実行されます。

直接オーバーロードせずに、代わりに `similarterm(::Type{<:T}, ...)` をオーバーロードしてください。
