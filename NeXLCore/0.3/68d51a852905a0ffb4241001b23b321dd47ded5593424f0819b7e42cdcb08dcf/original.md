```
atomicfraction(
    name::String,
    atomfracs::Union{Dict{Element,Float64},Pair{Element,Float64}...};
    properties::properties::Dict{Symbol, Any},
    atomicweights::Dict{Element,Float64},
    density::Union{Missing, AbstractFloat}=missing,
    description::Union{Missing, AbstractString}=missing,
    pedigree::Union{Missing, AbstractString}=missing,
    conductivity::Union{Missing, Symbol}=missing, # :Conductor, :Semiconductor, :Insulator
```

) # density, description, pedigree, conductivity

Build a Material from atomic fractions (or stoichiometries).
