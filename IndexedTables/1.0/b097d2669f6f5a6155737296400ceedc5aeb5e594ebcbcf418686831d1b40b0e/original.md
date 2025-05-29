```
columns(itr, select::Selection = Cols())
```

Select one or more columns from an iterable of rows as a tuple of vectors.

`select` specifies which columns to select. Refer to the [`select`](@ref) function for the available selection options and syntax.

`itr` can be `NDSparse`, `Columns`, `AbstractVector`, or their distributed counterparts.

# Examples

```
t = table(1:2, 3:4; names = [:x, :y])

columns(t)
columns(t, :x)
columns(t, (:x,))
columns(t, (:y, :x => -))
```
