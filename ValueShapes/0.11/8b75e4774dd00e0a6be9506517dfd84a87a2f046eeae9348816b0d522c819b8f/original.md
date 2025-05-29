```
unshaped(x)::AbstractVector{<:Real}
unshaped(x, shape::AbstractValueShape)::AbstractVector{<:Real}
```

Retrieve the unshaped underlying data of x, assuming x is a structured view (based on some [`AbstractValueShape`](@ref)) of a flat/unstructured real-valued data vector.

If `shape` is given, ensures that the shape of `x` is compatible with it. Specifying a shape may be necessary if the correct shape of `x` cannot be inferred from `x`, e.g. because `x` is assumed to have fewer degrees of freedom (because of constant components) than would be inferred from the plain value of `x`.

Example:

```julia
shape = NamedTupleShape(
    a = ScalarShape{Real}(),
    b = ArrayShape{Real}(2, 3)
)
data = [1, 2, 3, 4, 5, 6, 7]
x = shape(data)
@assert unshaped(x, shape) == data
@assert unshaped(x.a) == view(data, 1:1)
@assert unshaped(x.b) == view(data, 2:7)
```
