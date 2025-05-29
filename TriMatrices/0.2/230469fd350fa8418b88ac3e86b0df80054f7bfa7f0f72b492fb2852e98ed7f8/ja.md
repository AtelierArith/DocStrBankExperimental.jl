```
TriMatrix{T}(layout::TriLayout, undef, n::Integer; diag=zero(T))
TriMatrix(layout::TriLayout, undef, n::Integer; diag=0.)
```

初期化されていない `n` x `n` の `TriMatrix` を作成します。

`T` は指定されていない場合、デフォルトで `Float64` になります。
