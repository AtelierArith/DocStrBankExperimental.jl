```
derivative(f::BoundedQuadratic)
```

`f`の導関数、`f'`を返します。

# 例

```jldoctest
julia> bq = BoundedQuadratic(3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ ℝ

julia> derivative(bq)
BoundedQuadratic: f(x) = + 6.00000 x + 2.00000, ∀x ∈ ℝ

```
