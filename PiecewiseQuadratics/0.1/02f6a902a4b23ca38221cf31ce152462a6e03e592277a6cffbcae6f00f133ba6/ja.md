```
sum(f_list::Vector{PiecewiseQuadratic})
```

PiecewiseQuadraticのリストの合計を返します。

# 例

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -5., 0.),
                               BoundedQuadratic(0., 2., 0., 2., 0.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 2.00000]

julia> sum([f,f])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 10.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 4.00000 x , ∀x ∈ [0.00000, 2.00000]

julia> sum([f,-f])
Piecewise quadratic function:
BoundedQuadratic: f(x) = 0, ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = 0, ∀x ∈ [0.00000, 2.00000]

```
