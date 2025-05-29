```
getraster(T::Type{WorldClim{Elevation}}, [layer::Union{Tuple,Symbol}]; res::String="10m") => Union{Tuple,AbstractVector,String}
```

Download [`WorldClim`](@ref) [`Elevation`](@ref) data.

# Arguments

  * `layer`: `Symbol` or `Tuple` of `Symbol` from `(:elev,)`.    Without a `layer` argument, all layers will be downloaded, and a `NamedTuple` of paths returned.

# Keywords

  * `res`: `String` chosen from ("30s", "2.5m", "5m", "10m"), "10m" by default.

Returns the filepath/s of the downloaded or pre-existing files.
