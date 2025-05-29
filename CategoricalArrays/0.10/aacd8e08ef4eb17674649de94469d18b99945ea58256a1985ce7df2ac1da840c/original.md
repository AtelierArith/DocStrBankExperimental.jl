```
CategoricalMatrix{T}(undef, m::Int, n::Int; levels=nothing, ordered=false)
```

Construct an uninitialized `CategoricalMatrix` with levels of type `T <: Union{AbstractChar, AbstractString, Number}` and dimensions `dim`. The `ordered` keyword argument determines whether the array values can be compared according to the ordering of levels or not (see [`isordered`](@ref)).

```
CategoricalMatrix{T, R}(undef, m::Int, n::Int; levels=nothing, ordered=false)
```

Similar to definition above, but uses reference type `R` instead of the default type (`UInt32`).

```
CategoricalMatrix(A::AbstractMatrix; levels=nothing, ordered=false)
```

Construct a `CategoricalMatrix` with the values from `A` and the same element type.

The `levels` keyword argument can be a vector specifying possible values for the data (this is equivalent to but more efficient than calling [`levels!`](@ref) on the resulting array). If `levels` is omitted and the element type supports it, levels are sorted in ascending order; else, they are kept in their order of appearance in `A`. The `ordered` keyword argument determines whether the array values can be compared according to the ordering of levels or not (see [`isordered`](@ref)).

If `A` is already a `CategoricalMatrix`, its levels, orderedness and reference type are preserved unless explicitly overriden.
