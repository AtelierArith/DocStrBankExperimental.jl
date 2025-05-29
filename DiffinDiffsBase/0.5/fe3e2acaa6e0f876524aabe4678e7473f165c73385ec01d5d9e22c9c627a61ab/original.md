```
apply_and(d, by::Pair)
apply_and(d, bys::Pair...)
```

Apply a function that returns `true` or `false` elementwise to the specified column(s) in a `Tables.jl`-compatible table `d` and return the result. If an array instead of a function is provided, elementwise equality (`==`) comparison is applied between the column and the array. See also [`apply_and!`](@ref).

The way a function is specified is the same as how it is done with [`apply`](@ref). If multiple `Pair`s are provided, the returned array is obtained by combining arrays returned by each function through bitwise `and`.
