```
TransformedOutput(f, init; tspan::AbstractRange, kw...)
```

An output that stores the result of some function `f` of the grid/s.

# Arguments

  * `f`: a function or functor that accepts an `AbstractArray` or `NamedTuple` of   `AbstractArray` with names matching `init`. The `AbstractArray` will be a view into    the grid the same size as the init grids, removing any padding that has been added.
  * `init`: initialisation `Array` or `NamedTuple` of `Array`

# Keywords

  * `tspan`: `AbstractRange` timespan for the simulation
  * `aux`: NamedTuple of arbitrary input data. Use `get(data, Aux(:key), I...)`    to access from a `Rule` in a type-stable way.
  * `mask`: `BitArray` for defining cells that will/will not be run.
  * `padval`: padding value for grids with neighborhood rules. The default is `zero(eltype(init))`.

WARNING: This feature is experimental. It may change in future versions,  and may not be 100% reliable in all cases. Please file github issues if problems occur.
