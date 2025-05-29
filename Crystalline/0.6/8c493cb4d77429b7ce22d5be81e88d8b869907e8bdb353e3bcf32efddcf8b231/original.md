```julia
cosets(
    g::Crystalline.SiteGroup
) -> Array{Crystalline.SymOperation{D}, 1} where D

```

Return the left coset representatives of a `SiteGroup` `g` (in its parent space group).

The cosets generate the orbit of the Wyckoff position [`position(g)`](@ref) (see also [`orbit(::SiteGroup)`](@ref)) and furnish a left-coset decomposition of the underlying space group, jointly with the operations in `g` itself.

See also [`cosets(::AbstractVector, ::AbstractVector)`](@ref). This method is equivalent (but may return different representatives in general) to `cosets(spacegroup(sgnum), g)`.
