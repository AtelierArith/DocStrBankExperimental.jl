```
ShapedAsNTArray{T<:NamedTuple,...} <: AbstractArray{T,N}
```

View of an `AbstractArray{<:AbstractVector{<:Real},N}` as an array of `NamedTuple`s, according to a specified [`NamedTupleShape`](@ref).

`ShapedAsNTArray` implements the `Tables` API.

Constructors:

```
ShapedAsNTArray(
    data::AbstractArray{<:AbstractVector{<:Real},
    shape::NamedTupleShape
)

shape.(data)
```

The resulting `ShapedAsNTArray` shares memory with `data`:

```julia
using ValueShapes, ArraysOfArrays, Tables, TypedTables

X = [
    (a = 42, b = rand(1:9, 2, 3))
    (a = 11, b = rand(1:9, 2, 3))
]

shape = valshape(X[1])
data = nestedview(Array{Int}(undef, totalndof(shape), 2))
Y = shape.(data)
@assert Y isa ShapedAsNTArray
Y[:] = X
@assert Y[1] == X[1] == shape(data[1])
@assert Y.a == [42, 11]
Tables.columns(Y)
@assert unshaped.(Y) === data
@assert Table(Y) isa TypedTables.Table
```

Use `unshaped.(Y)` to access `data` directly.

`Tables.columns(Y)` will return a `NamedTuple` of columns. They will contain a copy the data, using a memory layout as contiguous as possible for each column.
