```
struct Scale
```

Represents a scaling scheme, akin to `StatsModels.AbstractContrasts`.  Pass as value in `Dict` as hints to `schema` (or as `contrasts` kwarg for `fit`).

## Examples

Can specify scale value to use:

```
julia> schema((x=collect(1:10), ), Dict(:x => Scale(5)))
StatsModels.Schema with 1 entry:
  x => x(scaled: 5))
```

You can use a function to compute the scale value:

julia> schema((x=collect(1:10), ), Dict(:x => Scale(mad))) StatsModels.Schema with 1 entry:   x => x(scaled: 3.71)

Or [`scale`](@ref) will be automatically computed if left out:

```
julia> schema((x=collect(1:10), ), Dict(:x => Scale()))
StatsModels.Schema with 1 entry:
  x => x(scaled: 3.03)
```
