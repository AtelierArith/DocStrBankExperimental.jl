```
reverse(f::BoundedQuadratic)
```

`f`を`y`軸に対して反転させます。つまり、`f(x)`が与えられたとき、`f(-x)`を返します。

参照: [`reverse!`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 2., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 2.00000]

julia> reverse(bq)
BoundedQuadratic: f(x) = 1.00000 x² - 1.00000 x + 1.00000, ∀x ∈ [-2.00000, 1.00000]

```
