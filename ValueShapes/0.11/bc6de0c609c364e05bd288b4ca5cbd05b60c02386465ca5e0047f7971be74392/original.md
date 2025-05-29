```
NamedTupleShape{names,...} <: AbstractValueShape
```

Defines the shape of a `NamedTuple` (resp.  set of variables, parameters, etc.).

Constructors:

```
NamedTupleShape(name1 = shape1::AbstractValueShape, ...)
NamedTupleShape(named_shapes::NamedTuple)
```

Example:

```julia
shape = NamedTupleShape(
    a = ScalarShape{Real}(),
    b = ArrayShape{Real}(2, 3),
    c = ConstValueShape(42)
)

data = VectorOfSimilarVectors{Float64}(shape)
resize!(data, 10)
rand!(flatview(data))
table = shape.(data)
fill!(table.a, 4.2)
all(x -> x == 4.2, view(flatview(data), 1, :))
```

See also the documentation of [`AbstractValueShape`](@ref).
