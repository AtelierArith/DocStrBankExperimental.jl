```julia
nlive(genealogy, lat, ωs; block_predicates, buffer)

```

与えられた緯度における（周辺的な）系譜の生存エッジの数。

`block_predicate` は直接 [`edges_interval`](@ref) に渡されます。

他に [`nlive!`](@ref) も参照してください。
