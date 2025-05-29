```
similarterm(::Type{T}, head, args)
```

型 `T` の同じクロージャのノードにある項を返し、`head` をヘッド、`args` を引数として使用します。デフォルトでは、これにより `head(args...)` が実行されます。
