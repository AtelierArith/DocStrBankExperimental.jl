```
CategoricalVector{T}(undef, m::Int; levels=nothing, ordered=false)
```

Construct an uninitialized `CategoricalVector` with levels of type `T <: Union{AbstractChar, AbstractString, Number}` and dimensions `dim`.

The `levels` keyword argument can be a vector specifying possible values for the data (this is equivalent to but more efficient than calling [`levels!`](@ref) on the resulting array). The `ordered` keyword argument determines whether the array values can be compared according to the ordering of levels or not (see [`isordered`](@ref)).

```
CategoricalVector{T, R}(undef, m::Int; levels=nothing, ordered=false)
```

Similar to definition above, but uses reference type `R` instead of the default type (`UInt32`).

```
CategoricalVector(A::AbstractVector; levels=nothing, ordered=false)
```

Construct a `CategoricalVector` with the values from `A` and the same element type.

The `levels` keyword argument can be a vector specifying possible values for the data (this is equivalent to but more efficient than calling [`levels!`](@ref) on the resulting array). If `levels` is omitted and the element type supports it, levels are sorted in ascending order; else, they are kept in their order of appearance in `A`. The `ordered` keyword argument determines whether the array values can be compared according to the ordering of levels or not (see [`isordered`](@ref)).

If `A` is already a `CategoricalVector`, its levels, orderedness and reference type are preserved unless explicitly overriden.
