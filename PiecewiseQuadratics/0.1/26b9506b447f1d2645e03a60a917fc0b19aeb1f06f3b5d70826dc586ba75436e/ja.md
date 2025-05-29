```
envelope(f::PiecewiseQuadratic)
```

`PiecewiseQuadratic` `f`の最大の凸下限を計算します。

# 例

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-Inf, 0., 0., 1., 0.),
                               BoundedQuadratic(0., 3., 0., 0., 0.)])
区分二次関数:
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [-Inf, 0.00000]
BoundedQuadratic: f(x) = 0, ∀x ∈ [0.00000, 3.00000]

julia> envelope(f)
区分二次関数:
BoundedQuadratic: f(x) = + 1.00000 x - 3.00000, ∀x ∈ [-Inf, 3.00000]

```
