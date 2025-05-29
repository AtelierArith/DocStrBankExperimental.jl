```
ValueAccessor{S<:AbstractValueShape}
```

A value accessor provides a means to access a value with a given shape stored in a flat real-valued data vector with a given offset position.

Constructor:

```
ValueAccessor{S}(shape::S, offset::Int)
```

The offset is relative to the first index of a flat data array, so if the value is stored at the beginning of the array, the offset will be zero.

An `ValueAccessor` can be used to index into a given flat data array.

Example:

```julia
acc = ValueAccessor(ArrayShape{Real}(2,3), 2)
valshape(acc) == ArrayShape{Real,2}((2, 3))
data = [1, 2, 3, 4, 5, 6, 7, 8, 9]
data[acc] == acc(data) == [3 5 7; 4 6 8]
```

Note: Subtypes of [`AbstractValueShape`](@ref) should specialize [`ValueShapes.vs_getindex`](@ref), [`ValueShapes.vs_unsafe_view`](@ref) and [`ValueShapes.vs_setindex!`](@ref) for their `ValueAccessor{...}`. Specializing `Base.getindex`, `Base.view`, `Base.unsafe_view` or `Base.setindex!` directly may result in method ambiguities with custom array tapes that specialize these functions in a very generic fashion.
