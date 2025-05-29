```
createfile(filename, field::Union{NCvar,Dict{String,NCvar}}, README;
            fillval=NaN, missval=NaN, itile=1, ntile=1)
```

Create NetCDF file and add variable + dimension definitions using either `NCDatasets.jl` or `NetCDF.jl`
