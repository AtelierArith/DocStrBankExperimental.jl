```
Derivative(sp::Space)
```

最初の導関数演算子を返します。これは `Derivative(sp,1)` に相当します。

# 例

```jldoctest
julia> Derivative(Chebyshev()) * Fun(x->x^2) ≈ Fun(x->2x)
true
```
