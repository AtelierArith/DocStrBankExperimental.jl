```
Image <: SingleGridRenderer

Image(f=identity; scheme=ObjectScheme(), zerocolor=nothing, maskcolor=nothing)
```

Converts output grids to a colorsheme.

# Arguments

  * `f`: a function to convert value from the grid to `Real`   oran `RGB`. `Real` will be scaled by minval/maxval and be colored by the `scheme`.   `RGB` is used directly in the output. This is useful for grids of complex objects,   but not necessary for numbers. The default is `identity`.

# Keywords

  * `scheme`: a ColorSchemes.jl colorscheme, [`ObjectScheme`](@ref) or object that defines   `Base.get(obj, val)` and returns a `Color` or a value that can be converted to `Color`   using `ARGB32(val)`.
  * `zerocolor`: a `Col` to use when values are zero, or `nothing` to ignore.
  * `maskcolor`: a `Color` to use when cells are masked, or `nothing` to ignore.
