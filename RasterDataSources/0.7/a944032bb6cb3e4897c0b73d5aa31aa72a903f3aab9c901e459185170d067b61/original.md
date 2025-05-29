```
getraster(T::Type{WorldClim{Weather}}, [layer::Union{Tuple,Symbol}]; date) => Union{String,Tuple{String},Vector{String}}
```

Download [`WorldClim`](@ref) [`Weather`](@ref) data, for `layer`/s in: `(:tmin, :tmax, :prec)`. Without a layer argument, all layers will be downloaded, and a `NamedTuple` of paths returned. 

# Keywords

  * `date`: a `Date` or `DateTime` object, a `Vector` of dates, or `Tuple` of start/end dates.   WorldClim Weather is available with a daily timestep.

Returns the filepath/s of the downloaded or pre-existing files.
