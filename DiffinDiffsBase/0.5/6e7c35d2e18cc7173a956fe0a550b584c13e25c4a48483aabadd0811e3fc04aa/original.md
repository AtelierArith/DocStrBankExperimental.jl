```
apply_and!(inds::BitVector, d, by::Pair)
apply_and!(inds::BitVector, d, bys::Pair...)
```

Apply a function that returns `true` or `false` elementwise to the specified column(s) in a `Tables.jl`-compatible table `d` and then update the elements in `inds` through bitwise `and` with the returned array. If an array instead of a function is provided, elementwise equality (`==`) comparison is applied between the column and the array. See also [`apply_and`](@ref).

The way a function is specified is the same as how it is done with [`apply`](@ref). If multiple `Pair`s are provided, `inds` are updated for each returned array through bitwise `and`.
