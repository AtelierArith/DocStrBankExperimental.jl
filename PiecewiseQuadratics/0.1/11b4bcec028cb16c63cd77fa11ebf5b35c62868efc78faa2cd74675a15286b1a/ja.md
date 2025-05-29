```
perspective(f::BoundedQuadratic, α::Real)
```

`f`のパースペクティブ関数を返します。すなわち、`f(x)`と`α`が与えられたとき、`α * f(x / α)`を返します。

注意: この操作にはドメインのスケーリングが必要です。

参照: [`perspective!`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> perspective(bq, 2.)
BoundedQuadratic: f(x) = 0.50000 x² + 1.00000 x + 2.00000, ∀x ∈ [-2.00000, 2.00000]

```
