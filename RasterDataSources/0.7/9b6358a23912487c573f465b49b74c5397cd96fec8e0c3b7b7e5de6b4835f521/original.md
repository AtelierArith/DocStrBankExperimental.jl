```
getraster(T::Type{CHELSA{Climate}}, [layer::Union{Tuple,Symbol}]; month) => Vector{String}
```

Download [`CHELSA`](@ref) [`Climate`](@ref) data. 

# Arguments

  * `layer` `Symbol` or `Tuple` of `Symbol` from `(:clt, :cmi, :hurs, :ncdf, :pet, :pr, :rsds, :sfcWind, :tas, :tasmax, :tasmin, :vpd)`.

# Keywords

  * `month`: `Integer` or `AbstractArray` of `Integer`. Chosen from `1:12`.

Returns the filepath/s of the downloaded or pre-existing files.
