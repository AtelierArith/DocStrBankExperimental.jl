```
struct ZScore
```

Represents a z-scoring scheme, akin to `StatsModels.AbstractContrasts`.  Pass as value in `Dict` as hints to `schema` (or as `contrasts` kwarg for `fit`).

## Examples

Can specify the center and scale values to use:

```
julia> schema((x=collect(1:10), ), Dict(:x => ZScore(; center=5, scale=3)))
StatsModels.Schema with 1 entry:
  x => x(centered: 5 scaled: 3)
```

Or scale will be automatically computed if left out:

```
julia> schema((x=collect(1:10), ), Dict(:x => ZScore()))
StatsModels.Schema with 1 entry:
  x => x(centered: 5.5 scaled: 3.03)
```
