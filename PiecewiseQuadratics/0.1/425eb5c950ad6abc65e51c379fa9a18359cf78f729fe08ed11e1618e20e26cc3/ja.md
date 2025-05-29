```
tilt(f::PiecewiseQuadratic, α::Real)
```

`f`を`α`だけ傾けます。これは線形係数`q`を`α`だけシフトします。

関連: [`tilt!`](@ref)

# 例

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -5., 0.),
                               BoundedQuadratic(0., 2., 0., 2., 0.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 2.00000]

julia> tilt(f, 5.)
Piecewise quadratic function:
BoundedQuadratic: f(x) = 0, ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 7.00000 x , ∀x ∈ [0.00000, 2.00000]

```
