```julia
sitegroups(sg::Crystalline.SpaceGroup{D}) -> Any

```

Return all site symmetry groups associated with a space group, specified either as  `sg :: SpaceGroup{D}` or by its conventional number `sgnum` and dimension `D` (if omitted, `D` defaults to 3).

See also [`sitegroup`](@ref) for calculation of the site symmetry group of a specific Wyckoff position.
