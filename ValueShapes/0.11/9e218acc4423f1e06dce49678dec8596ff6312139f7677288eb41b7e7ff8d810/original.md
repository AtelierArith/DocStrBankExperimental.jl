```
ArrayShape{T,N} <: AbstractValueShape
```

Describes the shape of `N`-dimensional arrays of type `T` and a given size.

Constructor:

```
ArrayShape{T}(dims::NTuple{N,Integer}) where {T,N}
ArrayShape{T}(dims::Integer...) where {T}
```

e.g.

```
shape = ArrayShape{Real}(2, 3)
```

See also the documentation of [`AbstractValueShape`](@ref).
