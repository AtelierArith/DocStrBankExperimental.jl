```
ShapedAsNT{names,...}
```

View of an `AbstractVector{<:Real}` as a mutable named tuple (though not) a `NamedTuple`, exactly), according to a specified [`NamedTupleShape`](@ref).

Constructors:

```
ShapedAsNT(data::AbstractVector{<:Real}, shape::NamedTupleShape)

shape(data)
```

The resulting `ShapedAsNT` shares memory with `data`:

```julia
x = (a = 42, b = rand(1:9, 2, 3))
shape = NamedTupleShape(
    ShapedAsNT,
    a = ScalarShape{Real}(),
    b = ArrayShape{Real}(2, 3)
)
data = Vector{Int}(undef, shape)
y = shape(data)
@assert y isa ShapedAsNT
y[] = x
@assert y[] == x
y.a = 22
@assert shape(data) == y
@assert unshaped(y) === data
```

Use `unshaped(x)` to access `data` directly.

See also [`ShapedAsNTArray`](@ref).
