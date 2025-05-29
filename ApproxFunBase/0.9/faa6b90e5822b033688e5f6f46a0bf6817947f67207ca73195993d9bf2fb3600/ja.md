```
Derivative(sp::Space, k::Int)
```

空間 `sp` に対する `k` 番目の導関数演算子を返します。

# 例

```jldoctest
julia> Derivative(Chebyshev(), 2) * Fun(x->x^4) ≈ Fun(x->12x^2)
true
```
