```
var(f::FiniteGP)
```

[`cov(f)`](@ref) の対角要素のみを計算します。

# 例

```jldoctest
julia> fx = GP(Matern52Kernel())(randn(10), 0.1);

julia> var(fx) == diag(cov(fx))
true
```
