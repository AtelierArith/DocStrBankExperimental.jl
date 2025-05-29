```
map_coefficients(f::Function, a::GenericQuadExpr)
```

[`GenericQuadExpr`](@ref) `a` の係数と定数項に `f` を適用し、新しい式を返します。

関連: [`map_coefficients_inplace!`](@ref)

## 例

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> a = @expression(model, x^2 + x + 1)
x² + x + 1

julia> map_coefficients(c -> 2 * c, a)
2 x² + 2 x + 2

julia> a
x² + x + 1
```
