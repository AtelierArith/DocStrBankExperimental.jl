```
GraphicOutput <: Output
```

Abstract supertype for [`Output`](@ref)s that display the simulation frames.

All `GraphicOutputs` must have a [`GraphicConfig`](@ref) object and define a [`showframe`](@ref) method.

See [`REPLOutput`](@ref) for an example.

# User Arguments for all `GraphicOutput`:

  * `init`: initialisation `AbstractArray` or `NamedTuple` of `AbstractArray`

# Minimum user keywords for all `GraphicOutput`:

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

## Internal keywords for constructors of objects extending `GraphicOutput`:

The default constructor will generate these objects and pass them to the inheriting  object constructor, which must accept the following keywords:

  * `frames`: a `Vector` of simulation frames (`NamedTuple` or `Array`).
  * `running`: A `Bool`.
  * `extent` an [`Extent`](@ref) object.
  * `graphicconfig` a [`GraphicConfig`](@ref)object.

Users can also pass in these entire objects if required.
