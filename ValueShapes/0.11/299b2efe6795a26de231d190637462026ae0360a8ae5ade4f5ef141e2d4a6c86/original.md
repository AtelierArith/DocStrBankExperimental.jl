```
ConstValueShape{T} <: AbstractValueShape
```

A `ConstValueShape` describes the shape of constant values of type `T`.

Constructor:

```
ConstValueShape(value)
```

`value` may be of arbitrary type, e.g. a constant scalar value or array:

```
ConstValueShape(4.2)
ConstValueShape([11 21; 12 22])
```

Shapes of constant values have zero degrees of freedom (see [`totalndof`](@ref)).

See also the documentation of [`AbstractValueShape`](@ref).
