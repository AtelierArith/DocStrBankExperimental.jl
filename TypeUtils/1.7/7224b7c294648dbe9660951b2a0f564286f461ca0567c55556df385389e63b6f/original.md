```
new_array(T, inds...) -> A
new_array(T, (inds...,)) -> A
```

create a new array with element type `T` and shape defined by `inds...`, a list of array dimension lengths and/or index ranges. The shape may also be specified as a tuple.

If `inds...` contains any index range other than `Base.OneTo`, an `OffsetArray{T}` is returned; otherwise an `Array{T}` is returned. In the former case, an exception is thrown if the package `OffsetArrays` has not been loaded.

Also see [`as_array_shape`](@ref), [`as_array_axes`](@ref), and [`as_array_size`](@ref).
