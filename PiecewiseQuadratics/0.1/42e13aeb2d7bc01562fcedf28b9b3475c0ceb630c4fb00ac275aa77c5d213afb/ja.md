```
get_tangent(f::BoundedQuadratic, x::Real)
```

新しい非制約の `BoundedQuadratic` を構築し、点 `x` における `f` の（非制約の）接線を表します。

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> tangent = get_tangent(bq, 0.5)
BoundedQuadratic: f(x) = + 2.00000 x + 0.75000, ∀x ∈ ℝ

```
