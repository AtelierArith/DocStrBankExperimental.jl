```
getraster(T::Type{WorldClim{Climate}}, [layer::Union{Tuple,Symbol}]; month, res::String="10m") => Vector{String}
```

Download [`WorldClim`](@ref) [`Climate`](@ref) data. 

# Arguments

  * `layer` `Symbol` or `Tuple` of `Symbol` from `(:tmin, :tmax, :tavg, :prec, :srad, :wind, :vapr)`.    Without a `layer` argument, all layers will be downloaded, and a `NamedTuple` of paths returned.

# Keywords

  * `month`: `Integer` or `AbstractArray` of `Integer`. Chosen from `1:12`.
  * `res`: `String` chosen from ("30s", "2.5m", "5m", "10m"), "10m" by default.

Returns the filepath/s of the downloaded or pre-existing files.
