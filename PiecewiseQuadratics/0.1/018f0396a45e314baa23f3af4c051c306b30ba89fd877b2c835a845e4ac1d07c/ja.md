```
scale(f::PiecewiseQuadratic, α::Real)
```

新しい `PiecewiseQuadratic` を返します。これは `α` によってスケーリングされています。つまり、`f(x)` と `α` が与えられたとき、`f(αx)` を返します。

注意: この操作はドメインのスケーリングを必要とします。

参照: [`scale!`](@ref)

# 例

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -1., 0.),
                               BoundedQuadratic(0., 1., 0., 1., 0.),
                               BoundedQuadratic(1., 5., 1., 1., 1.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, 1.00000]
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [1.00000, 5.00000]

julia> scale(f, 5)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-0.20000, 0.00000]
BoundedQuadratic: f(x) = + 5.00000 x , ∀x ∈ [0.00000, 0.20000]
BoundedQuadratic: f(x) = 25.00000 x² + 5.00000 x + 1.00000, ∀x ∈ [0.20000, 1.00000]

```
