```
Size(dims::Int...)
```

`Size` is used extensively throughout the `StaticArrays` API to describe *compile-time* knowledge of the size of an array. The dimensions are stored as a type parameter and are statically propagated by the compiler, resulting in efficient, type-inferrable code. For example, to create a static matrix of zeros, use `A = zeros(SMatrix{3,3})`. The static size of `A` can be obtained by `Size(A)`. (rather than `size(zeros(3,3))`, which returns `Base.Tuple{2,Int}`).

Note that if dimensions are not known statically (e.g., for standard `Array`s), [`Dynamic()`](@ref) should be used instead of an `Int`.

```
Size(a::AbstractArray)
Size(::Type{T<:AbstractArray})
```

The `Size` constructor can be used to extract static dimension information from a given array. For example:

```julia-repl
julia> Size(zeros(SMatrix{3, 4}))
Size(3, 4)

julia> Size(zeros(3, 4))
Size(StaticArrays.Dynamic(), StaticArrays.Dynamic())
```

This has multiple uses, including "trait"-based dispatch on the size of a statically-sized array. For example:

```julia
det(x::StaticMatrix) = _det(Size(x), x)
_det(::Size{(1,1)}, x::StaticMatrix) = x[1,1]
_det(::Size{(2,2)}, x::StaticMatrix) = x[1,1]*x[2,2] - x[1,2]*x[2,1]
# and other definitions as necessary
```
