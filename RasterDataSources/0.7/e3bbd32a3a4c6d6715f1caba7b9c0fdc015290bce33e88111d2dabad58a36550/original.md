```
getraster(source::Type{CHELSA{BioClim}}, [layer]; version = 2, [patch]) => Union{Tuple,String}
```

Download [`CHELSA`](@ref) [`BioClim`](@ref) data from [chelsa-climate.org](https://chelsa-climate.org/).

# Arguments

  * `layer`: `Integer` or tuple/range of `Integer` from `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)`,    or `Symbol`s form `(:bio1, :bio2, :bio3, :bio4, :bio5, :bio6, :bio7, :bio8, :bio9, :bio10, :bio11, :bio12, :bio13, :bio14, :bio15, :bio16, :bio17, :bio18, :bio19)`. Without a `layer` argument, all layers   will be downloaded, and a `NamedTuple` of paths returned.

# Keyword arguments

  * `version`: `Integer` indicating the CHELSA version, currently either `1` or `2`.
  * `patch`: `Integer` indicating the CHELSA patch number. Defaults to the latest patch (V1.2 and V2.1)

Returns the filepath/s of the downloaded or pre-existing files.
