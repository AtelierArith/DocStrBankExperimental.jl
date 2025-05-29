```
ArrayOutput <: Output

ArrayOutput(init; tspan::AbstractRange, [aux, mask, padval])
```

A simple output that stores each step of the simulation in a vector of arrays.

# Arguments

  * `init`: initialisation `AbstractArrayArray` or `NamedTuple` of `AbstractArrayArray`.

# Keywords (passed to [`Extent`](@ref))

  * `init`: initialisation `Array`/`NamedTuple` for grid/s.
  * `mask`: `BitArray` for defining cells that will/will not be run.
  * `aux`: NamedTuple of arbitrary input data. Use `aux(data, Aux(:key))` to access from   a `Rule` in a type-stable way.
  * `padval`: padding value for grids with neighborhood rules. The default is    `zero(eltype(init))`.
  * `tspan`: Time span range. Never type-stable, only access this in `modifyrule` methods

An `Extent` object can be also passed to the `extent` keyword, and other keywords will be ignored.
