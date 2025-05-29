```
levels!(A::CategoricalArray, newlevels::Vector; allowmissing::Bool=false)
```

Set the levels categorical array `A`. The order of appearance of levels will be respected by [`levels`](@ref DataAPI.levels), which may affect display of results in some operations; if `A` is ordered (see [`isordered`](@ref)), it will also be used for order comparisons using `<`, `>` and similar operators. Reordering levels will never affect the values of entries in the array.

If `A` accepts missing values (i.e. `eltype(A) >: Missing`) and `allowmissing=true`, entries corresponding to omitted levels will be set to `missing`. Else, `newlevels` must include all levels which appear in the data.
