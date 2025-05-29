```
littlegroups(sgnum::Integer, D::Union{Val{Int}, Integer}=Val(3)) 
                                                    -> Dict{String, LittleGroup{D}}
```

For given space group number `sgnum` and dimension `D`, return the associated little groups (`LittleGroups{D}`s) at high-symmetry k-points, lines, and planes (see also [`lgirreps`](@ref)).

Returns a `Dict` with little group **k**-point labels as keys and vectors of `LittleGroup{D}`s as values.

## Notes

A conventional crystallographic setting is assumed (as in [`spacegroup`](@ref)).

Unlike `spacegroup`, "centering"-copies of symmetry operations are not included in the returned `LittleGroup`s; as an example, space group 110 (body-centered, with centering symbol 'I') has a centering translation `[1/2,1/2,1/2]` in the conventional setting: the symmetry operations returned by `spacegroup` thus includes e.g. both `{1|0}` and  `{1|½,½,½}` while the symmetry operations returned by `littlegroups` only include `{1|0}` (and so on).

Currently, only `D = 3` is supported.

## References

The underlying data is sourced from the ISOTROPY dataset: see also [`lgirreps`](@ref).
