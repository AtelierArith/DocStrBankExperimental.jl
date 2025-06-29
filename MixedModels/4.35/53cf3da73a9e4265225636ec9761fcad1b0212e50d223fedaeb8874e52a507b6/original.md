```
struct Grouping <: StatsModels.AbstractContrasts end
```

A placeholder type to indicate that a categorical variable is only used for grouping and not for contrasts.  When creating a `CategoricalTerm`, this skips constructing the contrasts matrix which makes it robust to large numbers of levels, while still holding onto the vector of levels and constructing the level-to-index mapping (`invindex` field of the `ContrastsMatrix`.).

Note that calling `modelcols` on a `CategoricalTerm{Grouping}` is an error.

# Examples

```julia
julia> schema((; grp = string.(1:100_000)))
# out-of-memory error

julia> schema((; grp = string.(1:100_000)), Dict(:grp => Grouping()))
```
