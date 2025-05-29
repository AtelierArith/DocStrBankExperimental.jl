```
shift(f::BoundedQuadratic, δ::Real)
```

`f`を`δ`だけ`x`軸に沿ってシフトします。

注意: `δ > 0`の場合、これは右シフトです。`δ < 0`の場合、これは左シフトです。

参照: [`shift!`](@ref)

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 1., 1., 1., 1.)
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [-1.00000, 1.00000]

julia> shift(bq, 2.)
BoundedQuadratic: f(x) = 1.00000 x² - 3.00000 x + 3.00000, ∀x ∈ [1.00000, 3.00000]

```
