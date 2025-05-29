```
L_BiCM_reduced(m::BiCM)
```

Return the log-likelihood of the BiCM model `m` based on the computed maximum likelihood parameters.

# Examples

```jldoctest
# Use with DBCM model:
julia> G = corporateclub();

julia> model = BiCM(G);

julia> solve_model!(model);

julia> L_BiCM_reduced(model);

```

See also [`L_BiCM_reduced(::Vector, ::Vector, ::Vector, ::Vector, ::Vector, ::UnitRange, ::UnitRange, ::Int)`](@ref)
