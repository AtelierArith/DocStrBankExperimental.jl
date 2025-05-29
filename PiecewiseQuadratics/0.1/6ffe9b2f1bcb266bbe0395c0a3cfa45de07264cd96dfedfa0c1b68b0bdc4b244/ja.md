```
(f::BoundedQuadratic)(x::Real)
```

`f`を評価します `x` が `f` の定義域にある場合、そうでなければ `Inf` を返します。

# 例

```jldoctest
julia> bq = BoundedQuadratic(3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ ℝ

julia> bq(1.)
6.0

```
