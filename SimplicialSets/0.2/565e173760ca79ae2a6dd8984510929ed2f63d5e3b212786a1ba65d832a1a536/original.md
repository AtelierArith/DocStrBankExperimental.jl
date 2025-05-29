```
LoopGroupSimplex{T<:AbstractSimplex} <: AbstractSimplex

LoopGroupSimplex(x::T) where T <: AbstractSimplex
```

This type represents simplices in the Kan loop groups of the simplicial set with elements of type `T`. The latter simplicial set is assume to be reduced, meaning that it contains a single simplex of dimension `0`.

The constructor returns the simplex in the loop group determined by the simplex `x`, which must be of strictly positive dimension.

Iterating over a `LoopGroupSimplex{T}` yields its components, which are of type `LoopGroupGenerator{T}`.

See also [`SimplicialSets.LoopGroupGenerator`](@ref).

# Examples

```jldoctest
julia> using SimplicialSets: s, d

julia> x = SymbolicSimplex(:x, 2); y = LoopGroupSimplex(x)
⟨x[0,1,2]⟩

julia> d(y, 1), d(y, 0)
(⟨x[0,1]⟩, ⟨x[1,2]⁻¹,x[0,2]⟩)

julia> LoopGroupSimplex(s(x, 0))
⟨⟩
```
