```
savegif(filename::String, o::Output; kw...)
```

Write the output array to a gif.

# Arguments

  * `filename`: File path to save the gif file to.
  * `output`: An [`Output`](@ref) object. Note that to make a gif, the output should stores   frames, and run with `store=true`, and `@assert DynamicGrids.istored(o)` should pass.

# Keywords

[`ImageConfig`](@ref) keywords:

  * `minval`: Minimum value in the grid(s) to normalise for conversion to an RGB pixel.    A `Vector/Matrix` for multiple grids, matching the `layout` array.    Note: The default is `0`, and will not be updated automatically for the simulation.
  * `maxval`: Maximum value in the grid(s) to normalise for conversion to an RGB pixel.    A `Vector/Matrix` for multiple grids, matching the `layout` array.    Note: The default is `1`, and will not be updated automatically for the simulation.
  * `font`: `String` name of font to search for. A default will be guessed.
  * `text`: `TextConfig()` or `nothing` for no text. Default is `TextConfig(; font=font)`.
  * `scheme`: a ColorSchemes.jl colorscheme, [`ObjectScheme`](@ref) or object that defines   `Base.get(obj, val)` and returns a `Color` or a value that can be converted to `Color`   using `ARGB32(val)`.
  * `zerocolor`: a `Col` to use when values are zero, or `nothing` to ignore.
  * `maskcolor`: a `Color` to use when cells are masked, or `nothing` to ignore.
  * `renderer`: [`Renderer`](@ref) like [`Image`](@ref) or [`Layout`](@ref). Will be detected    automatically, and use `scheme`, `zerocolor` and `maskcolor` keywords if available.   Can be a `Vector/Matrix` for multiple grids, matching the `layout` array.
