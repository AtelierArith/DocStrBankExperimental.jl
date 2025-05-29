```
perspective(f::PiecewiseQuadratic, α::Real)
```

`f`のペースペクティブ関数を返します。すなわち、`f(x)`と`α`が与えられたとき、`α * f(x / α)`を返します。

注意: この操作にはドメインのスケーリングが必要です。

参照: [`perspective!`](@ref)

# 例

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -5., 0.),
                               BoundedQuadratic(0., 2., 0., 2., 0.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 2.00000]

julia> persp = perspective(f, 5.)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 5.00000 x , ∀x ∈ [-5.00000, 0.00000]
BoundedQuadratic: f(x) = + 2.00000 x , ∀x ∈ [0.00000, 10.00000]

```
