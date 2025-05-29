```
tilt(f::BoundedQuadratic, α::Real)
```

`f`を`α`だけ傾けたものを返します。これは線形係数`q`を`α`だけシフトします。

関連: [`tilt!`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> tilt(bq, 2.)
BoundedQuadratic: f(x) = 1.00000 x² + 3.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

```
