```
struct Center
```

Represents a centering scheme, akin to `StatsModels.AbstractContrasts`.  Pass as value in `Dict` as hints to `schema` (or as `contrasts` kwarg for `fit`).

## Examples

Can specify center value to use:

```
julia> schema((x=collect(1:10), ), Dict(:x => Center(5)))
StatsModels.Schema with 1 entry:
  x => center(x, 5)
```

You can use a function to compute the center value:

julia> schema((x=collect(1:10), ), Dict(:x => Center(median))) StatsModels.Schema with 1 entry:   x => x(centered: 5.5)

Or [`center`](@ref) will be automatically computed if omitted:

```
julia> schema((x=collect(1:10), ), Dict(:x => Center()))
StatsModels.Schema with 1 entry:
  x => center(x, 5.5)
```
