```
shift(f::PiecewiseQuadratic, δ::Real)
```

`f`を`δ`だけ`x`軸に沿ってシフトします。

注意: `δ > 0`の場合、これは右シフトです。`δ < 0`の場合、これは左シフトです。

参照: [`shift!`](@ref)

# 例

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -5., 0.),
                               BoundedQuadratic(0., 2., 0., 2., 0.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 2.00000]

julia> shift(f, 5.)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x + 25.00000, ∀x ∈ [4.00000, 5.00000]
BoundedQuadratic: f(x) = + 2.00000 x - 10.00000, ∀x ∈ [5.00000, 7.00000]

```
