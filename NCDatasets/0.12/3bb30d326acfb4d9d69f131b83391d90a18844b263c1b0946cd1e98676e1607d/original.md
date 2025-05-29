```
a = nomissing(da,value)
```

Retun the values of the array `da` of type `Array{Union{T,Missing},N}` as a regular Julia array `a` by replacing all missing value by `value` (converted to type `T`). This function is identical to `coalesce.(da,T(value))` where T is the element tyoe of `da`.

## Example:

```julia-repl
julia> nomissing([missing,1.,2.],NaN)
# returns [NaN, 1.0, 2.0]
```
