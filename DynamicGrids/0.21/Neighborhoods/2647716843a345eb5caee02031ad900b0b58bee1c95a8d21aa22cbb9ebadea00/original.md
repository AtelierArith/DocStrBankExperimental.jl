```
LayeredPositional <: AbstractPositional

LayeredPositional(layers::Positional...)
```

Sets of [`Positional`](@ref) neighborhoods that can have separate rules for each set.

`neighbors` for `LayeredPositional` returns a tuple of iterators for each neighborhood layer.
