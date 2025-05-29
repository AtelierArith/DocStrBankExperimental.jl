```
findmaximal(sitegs::AbstractVector{<:SiteGroup})
```

Given an `AbstractVector{<:SiteGroup}` over the distinct Wyckoff positions of a space group, return those `SiteGroup`s that are associated with a maximal Wyckoff positions.

Results are returned as a `view` into the input vector (i.e. as an  `AbstractVector{<:SiteGroup}`). The associated Wyckoff positions can be retrieved via [`position`](@ref).

## Definition

A Wyckoff position is maximal if its site symmetry group has higher order than the site symmetry groups of any "nearby" Wyckoff positions (i.e. Wyckoff positions that can be  connected, i.e. made equivalent, through parameter variation to the considered Wyckoff position).

## Example

```jldoctest
julia> sgnum = 5;

julia> D = 2;

julia> sg  = spacegroup(sgnum, Val(D));

julia> sitegs = sitegroups(sg)
2-element Vector{SiteGroup{2}}:
 [1] (4b: [α, β])
 [1, m₁₀] (2a: [0, β])

julia> only(findmaximal(sitegs))
SiteGroup{2} ⋕5 (c1m1) at 2a = [0, β] with 2 operations:
 1
 m₁₀
```
