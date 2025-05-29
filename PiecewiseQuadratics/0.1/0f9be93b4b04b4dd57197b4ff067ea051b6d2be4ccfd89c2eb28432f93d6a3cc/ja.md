```
scale(f::BoundedQuadratic, α::Real)
```

新しい `BoundedQuadratic` を返します。これは `α` によってスケーリングされています。つまり、`f(x)` と `α` が与えられたとき、`f(αx)` を返します。

注意: この操作はドメインのスケーリングを必要とします。

参照: [`scale!`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> scale(bq, 2.)
BoundedQuadratic: f(x) = 4.00000 x² + 2.00000 x + 1.00000, ∀x ∈ [-0.50000, 0.50000]

```
