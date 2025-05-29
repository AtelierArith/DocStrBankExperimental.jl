```
all_measures(model::InfiniteModel)::Vector{GeneralVariableRef}
```

Return the list of all measures added to `model`.

**Examples**

```julia-repl
julia> all_measures(model)
2-element Array{GeneralVariableRef,1}:
 ∫{t ∈ [0, 6]}[w(t, x)]
 𝔼{x}[w(t, x)]
```
