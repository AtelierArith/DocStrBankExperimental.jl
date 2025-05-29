```
Semiinteger(lower, upper)
```

[`MOI.Semiinteger`](@ref) セットのショートカットです。

このショートカットは、`lower` と `upper` を自動的に同じ型に昇格させ、JuMP モデルでサポートされている要素型に変換するため便利です。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x in Semiinteger(3, 5))
x

julia> print(model)
Feasibility
Subject to
 x ∈ MathOptInterface.Semiinteger{Int64}(3, 5)
```
