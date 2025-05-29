```
bags(k::Vector{<:Integer})
bags(k::Vector{T}) where T <: UnitRange{<:Integer}
bags(b::AbstractBags)
```

Construct an [`AbstractBags`](@ref) structure that is most suitable for the input ([`AlignedBags`](@ref) if possible, [`ScatteredBags`](@ref) otherwise).

# Examples

```jldoctest
julia> bags([1, 1, 3])
AlignedBags{Int64}(UnitRange{Int64}[1:2, 0:-1, 3:3])

julia> bags([2, 3, 1, 2])
ScatteredBags{Int64}([[3], [1, 4], [2]])

julia> bags([1:3, 4:5])
AlignedBags{Int64}(UnitRange{Int64}[1:3, 4:5])

julia> bags(ScatteredBags())
ScatteredBags{Int64}(Vector{Int64}[])
```

See also: [`AlignedBags`](@ref), [`ScatteredBags`](@ref).
