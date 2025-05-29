```
map_coefficients_inplace!(f::Function, a::GenericAffExpr)
```

[`GenericAffExpr`](@ref) `a` の係数と定数項に `f` を適用し、インプレースで更新します。

関連情報: [`map_coefficients`](@ref)

## 例

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x))
julia> a = GenericAffExpr(1.0, x => 1.0)
x + 1

julia> map_coefficients_inplace!(c -> 2 * c, a)
2 x + 2

julia> a
2 x + 2
```
