```
find_isomorphic_parent_pointgroup(g::AbstractVector{SymOperation{D}}) 
                                                --> PointGroup{D}, Vector{Int}, Bool
```

Given a group `g` (or a collection of operators, defining a group), identifies a "parent" point group that is isomorphic to `g`.

Three variables are returned:

  * `pg`: the identified "parent" point group, with operators sorted to match the sorting of `g`'s operators.
  * `Iᵖ²ᵍ`: a permutation vector which transforms the standard sorting of point group operations (as returned by [`pointgroup(::String)`](@ref)) to the operator sorting of `g`.
  * `equal`: a boolean, identifying whether the point group parts of `g` operations are identical (`true`) or merely isomorphic to the point group operations in `g`. In practice, this indicates whether `pg` and `g` are in the same setting or not.

## Implementation

The identification is made partly on the basis of comparison of operators (this is is sufficient for the `equal = true` case) and partly on the basis of comparison of  multiplication tables (`equal = false` case); the latter can be combinatorially slow if the sorting of operators is unlucky (i.e., if permutation between sortings in `g` and `pg` differ by many pairwise permutations).

Beyond mere isomorphisms of multiplication tables, the search also guarantees that all rotation orders are shared between `pg` and `g`; similarly, the rotation senses (e.g., 4⁺ & 4⁻ have opposite rotation senses or directions) are shared. This disambiguates point groups  that are intrinsically isomorphic to eachother, e.g. "m" and "-1", but which still differ in their spatial interpretation.

## Properties

The following properties hold for `g`, `pg`, and `Iᵖ²ᵍ`:

```jl
pg, Iᵖ²ᵍ, equal = find_isomorphic_parent_pointgroup(g)
@assert MultTable(pg) == MultTable(pointgroup(g))
pg′ = pointgroup(label(pg), dim(pg)) # "standard" sorting
@assert pg′[Iᵖ²ᵍ] == pg
```

If `equal = true`, the following also holds:

```jl
pointgroup(g) == operations(pg) == operations(pg′)[Iᵖ²ᵍ]
```

## Example

```jl
sgnum = 141
wp    = wyckoffs(sgnum, Val(3))[end] # 4a Wyckoff position
sg    = spacegroup(sgnum, Val(3))
siteg = sitegroup(sg, wp)
pg, Iᵖ²ᵍ, equal = find_isomorphic_parent_pointgroup(siteg)
```
