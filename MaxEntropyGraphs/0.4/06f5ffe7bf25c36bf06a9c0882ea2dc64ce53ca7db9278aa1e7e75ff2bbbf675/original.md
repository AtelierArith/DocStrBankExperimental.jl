```
L_DBCM_reduced(m::DBCM)
```

Return the log-likelihood of the DBCM model `m` based on the computed maximum likelihood parameters.

# Examples

```jldoctest
# Use with DBCM model:
julia> G = MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques());

julia> model = DBCM(G);

julia> solve_model!(model);

julia> L_DBCM_reduced(model);

```

See also [`L_DBCM_reduced(::Vector, ::Vector, ::Vector, ::Vector, ::Vector, ::Vector)`](@ref)
