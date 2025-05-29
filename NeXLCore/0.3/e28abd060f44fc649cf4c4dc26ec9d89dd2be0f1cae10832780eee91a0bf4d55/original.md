```
material(
    name::AbstractString,
    massfrac::Dict{Element,U};
    properties::Union{Missing,Dict{Symbol,Any}} = missing,
    atomicweights::Union{Missing, Dict{Element,Float64}} = missing,
    density::Union{Missing,AbstractFloat} = missing,
    description::Union{Missing,AbstractString} = missing,
    pedigree::Union{Missing,AbstractString} = missing,
    conductivity::Union{Missing,Symbol} = missing, # :Conductor, :Semiconductor, :Insulator
)
material(
    name::AbstractString,
    massfrac::Dict{Element,<:AbstractFloat};
    properties::Dict{Symbol,Any}=Dict{Symbol,Any)(),
    atomicweights::Dict{Element, <:AbstractFloat}=Dict{Element,Float64}(),
    density::Union{Missing, AbstractFloat}=missing,
    description::Union{Missing, AbstractString}=missing,
    pedigree::Union{Missing, AbstractString}=missing,
    conductivity::Union{Missing, Symbol}=missing, # :Conductor, :Semiconductor, :Insulator
)
```

Constuct a material from mass fraction pairs.
