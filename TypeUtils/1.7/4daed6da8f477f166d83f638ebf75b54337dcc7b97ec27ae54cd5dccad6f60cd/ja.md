```
as_eltype(T, A) -> B
```

は、そのエントリを型 `T` に遅延的に変換する配列を生成します。より具体的には、`B[i]` の呼び出しは `as(T,A[i])` を返します。

変換を一度だけ即座に行うには、[`convert_eltype(T, A)`](@ref convert_eltype) の使用を検討してください。
