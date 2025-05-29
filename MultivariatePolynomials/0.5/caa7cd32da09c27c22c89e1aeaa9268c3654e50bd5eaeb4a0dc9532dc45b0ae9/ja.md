```
primitive_univariate_gcd!(p::_APL, q::_APL, algo::AbstractUnivariateGCDAlgorithm)
```

原始多項式 `p` と `q` の `gcd` を、[`AbstractUnivariateGCDAlgorithm`](@ref) のサブタイプであるアルゴリズム `algo` を使用して返します。この関数は `p` または `q` を変更する可能性があります。
