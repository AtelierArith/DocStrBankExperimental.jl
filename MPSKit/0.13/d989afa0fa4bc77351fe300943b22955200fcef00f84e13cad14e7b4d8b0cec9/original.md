```
const MultilineMPS = Multiline{<:InfiniteMPS}
```

Type that represents multiple lines of `InfiniteMPS` objects.

# Constructors

```
MultilineMPS(mpss::AbstractVector{<:InfiniteMPS})
MultilineMPS([f, eltype], physicalspaces::Matrix{<:Union{S, CompositeSpace{S}},
             virtualspaces::Matrix{<:Union{S, CompositeSpace{S}}) where
             {S<:ElementarySpace}
MultilineMPS(As::AbstractMatrix{<:GenericMPSTensor}; kwargs...)
MultilineMPS(ALs::AbstractMatrix{<:GenericMPSTensor}, 
             C₀::AbstractVector{<:MPSBondTensor}; kwargs...)
```

See also: [`Multiline`](@ref)
