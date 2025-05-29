```
derivative(f::BoundedQuadratic, x::Real)
```

`f`の`x`における導関数、`f'(x)`を評価します。

# 例

```jldoctest
julia> bq = BoundedQuadratic(3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ ℝ

julia> derivative(bq, 2.)
14.0

```
