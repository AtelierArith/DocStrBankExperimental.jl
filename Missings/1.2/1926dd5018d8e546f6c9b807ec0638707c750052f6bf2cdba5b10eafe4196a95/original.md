```
disallowmissing(x::AbstractArray)
```

Return an array equal to `x` not allowing for [`missing`](@ref) values, i.e. with an element type equal to `nonmissingtype(eltype(x))`.

When possible, the result will share memory with `x` (as with [`convert`](@ref)). If `x` contains missing values, a `MethodError` is thrown.

See also: [`allowmissing`](@ref)
