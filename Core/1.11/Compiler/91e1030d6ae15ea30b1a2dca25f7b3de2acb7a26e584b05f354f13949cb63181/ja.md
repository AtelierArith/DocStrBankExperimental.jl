```
canonicalize_typeassert!(compact::IncrementalCompact, idx::Int, stmt::Expr)
```

`X = typeassert(Y, T)::S` を `typeassert(Y, T); X = π(Y, S)` に正規化します。これにより、その後の分析は後者の形式のみを扱えばよくなります。

注意：推論は `S` に対して `T` よりも正確な型を持っている可能性がありますが、ここから先はそれを使用することに問題はありません。バックエンドのために、値を返さないように定義された `typeassert` のバージョンを持つべきかもしれません。
