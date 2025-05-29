```
SingleParam{T}
```

Struct designed to contain single parameters. Basically a vector with some extra info.

## Creation:

```julia-repl
julia> mw = SingleParam("molecular weight",["water","ammonia"],[18.01,17.03])
SingleParam{Float64}("molecular weight") with 2 components:
 "water" => 18.01
 "ammonia" => 17.03
julia> mw.values
2-element Vector{Float64}:
 18.01
 17.03
julia> mw.components
2-element Vector{String}:
 "water"
 "ammonia"
julia> mw2 = SingleParam(mw,"new name")
SingleParam{Float64}("new name") with 2 components:
 "water" => 18.01
 "ammonia" => 17.03
julia> has_oxigen = [true,false]; has_o = SingleParam(mw2,has_oxigen)
SingleParam{Bool}("new name") with 2 components:
 "water" => true
 "ammonia" => false
```

## Example usage in models:

```
function molecular_weight(model,molar_frac)
    mw = model.params.mw.values
    res = zero(eltype(molarfrac))
    for i in @comps #iterating through all components
        res += molar_frac[i]*mw[i]
    end
    return res
end
```
