```
sparse_jacobian!(J::AbstractMatrix, ad::AbstractADType, sd::AbstractSparsityDetection,
    f, x; fx=nothing)
sparse_jacobian!(J::AbstractMatrix, ad::AbstractADType, sd::AbstractSparsityDetection,
    f!, fx, x)
```

`sparse_jacobian_cache` と `sparse_jacobian!` を順次呼び出して、`f` の `x` におけるヤコビアンを計算します。`f` のヤコビアンが正確に1回だけ計算される場合にこれを使用します。それ以外の場合は、最初に `sparse_jacobian_cache` を1回使用してキャッシュを生成し、同じキャッシュを使用して `sparse_jacobian!` でヤコビアンを計算します。
