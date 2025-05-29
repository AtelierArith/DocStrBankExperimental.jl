```
classes(x)
```

All the categorical elements with the same pool as `x` (including `x`), returned as a list, with an ordering consistent with the pool. Here `x` has `CategoricalValue` type, and `classes(x)` is a vector of the same eltype. Note that `x in classes(x)` is always true.

Not to be confused with `levels(x.pool)`. See the example below.

```julia-repl
julia> v = categorical(["c", "b", "c", "a"])
4-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "c"
 "b"
 "c"
 "a"

julia> levels(v)
3-element Vector{String}:
 "a"
 "b"
 "c"

julia> x = v[4]
CategoricalArrays.CategoricalValue{String, UInt32} "a"

julia> classes(x)
3-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "a"
 "b"
 "c"

julia> levels(x.pool)
3-element Vector{String}:
 "a"
 "b"
 "c"
```
