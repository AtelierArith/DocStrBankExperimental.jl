```
getraster(T::Type{WorldClim{BioClim}}, [layer::Union{Tuple,AbstractVector,Integer}]; res::String="10m") => Union{Tuple,AbstractVector,String}
```

Download [`WorldClim`](@ref) [`BioClim`](@ref) data.

# Arguments

  * `layer`: `Integer` or tuple/range of `Integer` from `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)`.    or `Symbol`s from `(:bio1, :bio2, :bio3, :bio4, :bio5, :bio6, :bio7, :bio8, :bio9, :bio10, :bio11, :bio12, :bio13, :bio14, :bio15, :bio16, :bio17, :bio18, :bio19)`. Without a `layer` argument, all layers   will be downloaded, and a `NamedTuple` of paths returned.

# Keywords

  * `res`: `String` chosen from ("30s", "2.5m", "5m", "10m"), "10m" by default.

Returns the filepath/s of the downloaded or pre-existing files.
