```
CircularVector{T,A} <: AbstractVector{T}
```

One-dimensional array backed by an `AbstractArray{T, 1}` of type `A` with fixed size and circular indexing. Alias for [`CircularArray{T,1,A}`](@ref).

```
array[index] == array[mod1(index, length)]
```
