```
Semicontinuous(lower, upper)
```

[`MOI.Semicontinuous`](@ref) セットのショートカットです。

このショートカットは、`lower` と `upper` を自動的に同じ型に昇格させ、JuMP モデルがサポートする要素型に変換するため便利です。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x in Semicontinuous(1, 2))
x

julia> print(model)
Feasibility
Subject to
 x ∈ MathOptInterface.Semicontinuous{Int64}(1, 2)
```
