```
restrict_dom(f::BoundedQuadratic, dom::Interval)
restrict_dom(f::BoundedQuadratic, lb::Real, ub::Real)
```

渡されたドメインの交差に制限された新しい BoundedQuadratic を返します。

参照: [`restrict_dom!`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(-10., 10., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-10.00000, 10.00000]

julia> restrict_dom(bq, 2., 3.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [2.00000, 3.00000]

```
