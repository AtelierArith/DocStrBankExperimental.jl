```
inner(M::FixedRankMatrices, p::SVDMPoint, X::UMVTangentVector, Y::UMVTangentVector)
```

`X`と`Y`の内積を、[`FixedRankMatrices`](@ref) `M`の点`p`の接空間で計算します。これは埋め込みから継承されており、`X`と`Y`の要素（`U`、`Vt`、`M`）に対して`dot`を使用して計算できます。
