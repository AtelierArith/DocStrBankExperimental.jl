```
is_almost_point(f::BoundedQuadratic)
```

`lb ≈ ub` の場合、BoundedQuadratic がほぼ単一の点で定義されている場合は `true` を返します。

参照: [`is_point`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(5., 5. + 1e-14, 3., 2., 1.)
BoundedQuadratic: f(x) = 3.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [5.00000, 5.00000]

julia> is_point(bq)
false

julia> is_almost_point(bq)
true

```
