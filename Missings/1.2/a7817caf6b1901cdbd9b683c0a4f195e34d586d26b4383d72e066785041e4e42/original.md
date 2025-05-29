```
allowmissing(x::AbstractArray)
```

Return an array equal to `x` allowing for [`missing`](@ref) values, i.e. with an element type equal to `Union{eltype(x), Missing}`.

When possible, the result will share memory with `x` (as with [`convert`](@ref)).

See also: [`disallowmissing`](@ref)
