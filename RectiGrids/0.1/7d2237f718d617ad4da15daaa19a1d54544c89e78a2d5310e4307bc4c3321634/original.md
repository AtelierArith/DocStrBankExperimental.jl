```
grid([T], xs, ys, ...) -> RectiGrid
grid([T], x=xs, y=ys, ...) -> RectiGrid
```

Create a `RectiGrid` object representing a rectilinear grid. Implements `AbstractArray` and `KeyedArray` interfaces.

Pass positional arguments `xs, ys, ...` for a grid with unnamed dimensions, or keyword arguments `x=xs, y=ys, ...` for named dimensions.

Type `T` can be `Tuple`, or a type with a `T(::Tuple)` constructor (e.g. `SVector`), or `NamedTuple` when dimensions are named.
