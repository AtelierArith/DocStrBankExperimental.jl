```
getraster(source::Type{AWAP}, [layer]; date)
```

Download data from the [`AWAP`](@ref) weather dataset, from [www.csiro.au/awap](http://www.csiro.au/awap/). 

The AWAP dataset contains ASCII `.grid` files.

# Arguments

  * `layer` `Symbol` or `Tuple` of `Symbol` for `layer`s in `(:solar, :rainfall, :vprpress09, :vprpress15, :tmin, :tmax)`. Without a    `layer` argument, all layers will be downloaded, and a `NamedTuple` of paths returned.

# Keywords

  * `date`: a `DateTime`, `AbstractVector` of `DateTime` or a `Tuple` of start and end dates.   For multiple dates, A `Vector` of multiple filenames will be returned.   AWAP is available with a daily timestep.

# Example

Download rainfall for the first month of 2001:

```julia
julia> getraster(AWAP, :rainfall; date=Date(2001, 1, 1):Day(1):Date(2001, 1, 31))

31-element Vector{String}:
 "/your/path/AWAP/rainfall/totals/20010101.grid"
 "/your/path/AWAP/rainfall/totals/20010102.grid"
 ...
 "/your/path/AWAP/rainfall/totals/20010131.grid"
```

Returns the filepath/s of the downloaded or pre-existing files.
