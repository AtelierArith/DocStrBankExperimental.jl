```
Extent <: AbstractExtent

Extent(init, mask, aux, padval, tspan)
Extent(; init, tspan, mask=nothing, aux=nothing, padval=zero(eltype(init)), kw...)
```

Container for extensive variables: spatial and timeseries data. These are kept separate from rules to allow application of rules to alternate spatial and temporal contexts.

Extent is not usually constructed directly by users, but it can be passed to `Output` constructors instead of `init`, `mask`, `aux` and `tspan`.

# Arguments/Keywords

  * `init`: initialisation `Array`/`NamedTuple` for grid/s.
  * `mask`: `BitArray` for defining cells that will/will not be run.
  * `aux`: NamedTuple of arbitrary input data. Use `aux(data, Aux(:key))` to access from   a `Rule` in a type-stable way.
  * `padval`: padding value for grids with neighborhood rules. The default is    `zero(eltype(init))`.
  * `tspan`: Time span range. Never type-stable, only access this in `modifyrule` methods
