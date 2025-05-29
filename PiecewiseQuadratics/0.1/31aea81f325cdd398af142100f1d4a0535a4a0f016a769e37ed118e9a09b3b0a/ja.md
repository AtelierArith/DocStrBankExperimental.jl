```
extend_dom(f::BoundedQuadratic)
```

`f`の非制約バージョンを返します。

参照: [`extend_dom!`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> extend_dom(bq)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ ℝ

```
