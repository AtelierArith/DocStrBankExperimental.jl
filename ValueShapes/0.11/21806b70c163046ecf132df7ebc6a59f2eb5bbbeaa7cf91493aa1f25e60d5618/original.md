```
abstract type AbstractValueShape
```

An `AbstractValueShape` combines type and size information.

Subtypes are defined for shapes of scalars (see [`ScalarShape`](@ref)), arrays (see [`ArrayShape`](@ref)), constant values (see [`ConstValueShape`](@ref)) and `NamedTuple`s (see [`NamedTupleShape`](@ref)).

Subtypes of `AbstractValueShape` must support `eltype`, `size` and [`totalndof`](@ref).

Value shapes can be used as constructors to generate values of the given shape with undefined content. If the element type of the shape is an abstract or union type, a suitable concrete type will be chosen automatically, if possible (see [`ValueShapes.default_datatype`](@ref)):

```julia
shape = ArrayShape{Real}(2,3)
A = shape(undef)
typeof(A) == Array{Float64,2}
size(A) == (2, 3)
valshape(A) == ArrayShape{Float64}(2,3)
```

Use

```
(shape::AbstractValueShape)(data::AbstractVector{<:Real})::eltype(shape)
```

to view a flat vector of anonymous real values as a value of the given shape:

```julia
data = [1, 2, 3, 4, 5, 6]
shape(data) == [1 3 5; 2 4 6]
```

In return,

```
Base.Vector{<:Real}(undef, shape::AbstractValueShape)
```

will create a suitable uninitialized vector of the right length to hold such flat data for the given shape. If no type `T` is given, a suitable data type will be chosen automatically.

When dealing with multiple vectors of flattened data, use

```
shape.(data::ArraysOfArrays.AbstractVectorOfSimilarVectors)
```

ValueShapes supports this via specialized broadcasting.

In return,

```
ArraysOfArrays.VectorOfSimilarVectors{<:Real}(shape::AbstractValueShape)
```

will create a suitable vector (of length zero) of vectors that can hold flattened data for the given shape. The result will be a `VectorOfSimilarVectors` wrapped around a 2-dimensional `ElasticArray`. This way, all data is stored in a single contiguous chunk of memory.

`AbstractValueShape`s can be compared with `<=` and `>=`, with semantics that are similar to compare type with `<:` and `>:`:

```julia
a::AbstractValueShape <= b::AbstractValueShape == true
```

implies that values of shape `a` are can be used in contexts that expect values of shape `b`. E.g.:

```julia
(ArrayShape{Float64}(4,5) <= ArrayShape{Real}(4,5)) == true
(ArrayShape{Float64}(4,5) <= ArrayShape{Integer}(4,5)) == false
(ArrayShape{Float64}(2,2) <= ArrayShape{Float64}(3,3)) == false
(ScalarShape{Real}() >= ScalarShape{Int}()) == true
```
