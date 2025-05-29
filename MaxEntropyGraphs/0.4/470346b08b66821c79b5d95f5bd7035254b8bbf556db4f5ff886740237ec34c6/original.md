```
L_UBCM_reduced(m::UBCM)
```

Return the log-likelihood of the UBCM model `m` based on the computed maximum likelihood parameters.

# Examples

```jldoctest
# Use with UBCM model:
julia> G = MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate);

julia> model = UBCM(G);

julia> solve_model!(model);

julia> L_UBCM_reduced(model)
-168.68325136302832
```

See also [`L_UBCM_reduced(::Vector, ::Vector, ::Vector)`](@ref)
