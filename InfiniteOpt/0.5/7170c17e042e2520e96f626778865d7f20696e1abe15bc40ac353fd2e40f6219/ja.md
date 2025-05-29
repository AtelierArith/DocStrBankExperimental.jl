```
all_measures(model::InfiniteModel)::Vector{GeneralVariableRef}
```

`model`に追加されたすべての測度のリストを返します。

**例**

```julia-repl
julia> all_measures(model)
2-element Array{GeneralVariableRef,1}:
 ∫{t ∈ [0, 6]}[w(t, x)]
 𝔼{x}[w(t, x)]
```
