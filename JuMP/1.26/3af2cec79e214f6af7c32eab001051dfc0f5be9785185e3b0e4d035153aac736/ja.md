```
map_coefficients(f::Function, a::GenericAffExpr)
```

[`GenericAffExpr`](@ref) `a` の係数と定数項に `f` を適用し、新しい式を返します。

関連: [`map_coefficients_inplace!`](@ref)

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> a = GenericAffExpr(1.0, x => 1.0)
x + 1

julia> map_coefficients(c -> 2 * c, a)
2 x + 2

julia> a
x + 1
```
