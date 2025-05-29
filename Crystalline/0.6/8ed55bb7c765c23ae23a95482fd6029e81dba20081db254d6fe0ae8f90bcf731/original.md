```
irreps(n::AbstractSymmetryVector{D}) -> AbstractVector{<:Collection{<:AbstractIrrep{D}}}
```

Return the irreps referenced by `n`. 

The returned value is an `AbstractVector` of `Collection{<:AbstractIrrep}`s, with irreps for distinct groups, usually associated with specific **k**-manifolds, belonging to the same `Collection`.

See also [`multiplicities(::AbstractSymmetryVector)`](@ref).
