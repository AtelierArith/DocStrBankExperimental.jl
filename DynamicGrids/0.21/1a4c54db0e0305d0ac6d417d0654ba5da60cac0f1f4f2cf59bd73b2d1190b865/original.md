```
REPLOutput <: GraphicOutput

REPLOutput(init; tspan, kw...)
```

An output that is displayed directly in the REPL. It can either store or discard simulation frames.

# Arguments:

  * `init`: initialisation `AbstractArrayArray` or `NamedTuple` of `AbstractArrayArray`.

# Keywords

  * `color`: a color from Crayons.jl
  * `cutoff`: `Real` cutoff point to display a full or empty cell. Default is `0.5`
  * `style`: `CharStyle` `Block()` or `Braile()` printing. `Braile` uses 1/4 the screen space of `Block`.

## [`Extent`](@ref) keywords:

  * `init`: initialisation `Array`/`NamedTuple` for grid/s.
  * `mask`: `BitArray` for defining cells that will/will not be run.
  * `aux`: NamedTuple of arbitrary input data. Use `aux(data, Aux(:key))` to access from   a `Rule` in a type-stable way.
  * `padval`: padding value for grids with neighborhood rules. The default is    `zero(eltype(init))`.
  * `tspan`: Time span range. Never type-stable, only access this in `modifyrule` methods

An `Extent` object can be also passed to the `extent` keyword, and other keywords will be ignored.

## [`GraphicConfig`](@ref) keywords:

  * `fps::Real`: Frames per second.
  * `store::Bool`: Whether to store frames like `ArrayOutput` or to disgard   them after visualising. Very long simulation runs may fill available    memory when `store=true`.

A `GraphicConfig` object can be also passed to the `graphicconfig` keyword, and other keywords will be ignored.

e `GraphicConfig` object can be also passed to the `graphicconfig` keyword, and other keywords will be ignored.
