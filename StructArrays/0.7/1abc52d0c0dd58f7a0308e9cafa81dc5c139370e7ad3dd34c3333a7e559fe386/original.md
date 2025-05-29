```
StructArray{T,N,C,I} <: AbstractArray{T, N}
```

A type that stores an `N`-dimensional array of structures of type `T` as a structure of arrays.

  * `getindex` and `setindex!` are overloaded to get/set values of type `T`.
  * `getproperty` is overloaded to return individual field arrays.

# Fields

  * `components`: a `NamedTuple` or `Tuple` of the arrays used by each field. These can be accessed by [`components(x)`](@ref).
