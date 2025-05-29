```
ImageOutput <: GraphicOutput
```

Abstract supertype for Graphic outputs that display the simulation frames as RGB images.

`ImageOutput`s must have [`Extent`](@ref), [`GraphicConfig`](@ref)  and [`ImageConfig`](@ref) components, and define a [`showimage`](@ref) method.

See [`GifOutput`](@ref) for an example.

Although the majority of the code is maintained here to enable sharing and reuse, most `ImageOutput`s are not provided in DynamicGrids.jl to avoid heavy dependencies on graphics libraries. See [DynamicGridsGtk.jl](https://github.com/cesaraustralia/DynamicGridsGtk.jl) and [DynamicGridsInteract.jl](https://github.com/cesaraustralia/DynamicGridsInteract.jl) for implementations.

# User Arguments for all `GraphicOutput`:

  * `init`: initialisation `AbstractArray` or `NamedTuple` of `AbstractArray`

# Minimum user keywords for all `ImageOutput`:

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

## [`ImageConfig`](@ref) keywords:

  * `minval`: Minimum value in the grid(s) to normalise for conversion to an RGB pixel.    A `Vector/Matrix` for multiple grids, matching the `layout` array.    Note: The default is `0`, and will not be updated automatically for the simulation.
  * `maxval`: Maximum value in the grid(s) to normalise for conversion to an RGB pixel.    A `Vector/Matrix` for multiple grids, matching the `layout` array.    Note: The default is `1`, and will not be updated automatically for the simulation.
  * `font`: `String` name of font to search for. A default will be guessed.
  * `text`: `TextConfig()` or `nothing` for no text. Default is `TextConfig(; font=font)`.
  * `scheme`: a ColorSchemes.jl colorscheme, [`ObjectScheme`](@ref) or object that defines   `Base.get(obj, val)` and returns a `Color` or a value that can be converted to `Color`   using `ARGB32(val)`.
  * `zerocolor`: a `Col` to use when values are zero, or `nothing` to ignore.
  * `maskcolor`: a `Color` to use when cells are masked, or `nothing` to ignore.
  * `renderer`: [`Renderer`](@ref) like [`Image`](@ref) or [`Layout`](@ref). Will be detected    automatically, and use `scheme`, `zerocolor` and `maskcolor` keywords if available.   Can be a `Vector/Matrix` for multiple grids, matching the `layout` array.

An `ImageConfig` object can be also passed to the `imageconfig` keyword, and other keywords will be ignored.

## Internal keywords for constructors of objects extending `GraphicOutput`:

The default constructor will generate these objects and pass them to the inheriting  object constructor, which must accept the following keywords:

  * `frames`: a `Vector` of simulation frames (`NamedTuple` or `Array`).
  * `running`: A `Bool`.
  * `extent` an [`Extent`](@ref) object.
  * `graphicconfig` a [`GraphicConfig`](@ref)object.
  * `imageconfig` a [`ImageConfig`](@ref)object.

Users can also pass in these entire objects if required.
