```
rows(itr, select = Cols())
```

Select one or more fields from an iterable of rows as a vector of their values.  Refer to the [`select`](@ref) function for selection options and syntax.

`itr` can be [`NDSparse`](@ref), `StructArrays.StructVector`, `AbstractVector`, or their distributed counterparts.

# Examples

```
t = table([1,2],[3,4], names=[:x,:y])
rows(t)
rows(t, :x)
rows(t, (:x,))
rows(t, (:y, :x => -))
```
