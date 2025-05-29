```
vtcounteq(x::AbstractArray, y::AbstractArray; dims=:)
```

Count the number of elements for which `xᵢ == yᵢ` returns `true` on the vectors corresponding to the slices along the dimension `dims`. Threaded.

See also: [`vtcountne`](@ref)
