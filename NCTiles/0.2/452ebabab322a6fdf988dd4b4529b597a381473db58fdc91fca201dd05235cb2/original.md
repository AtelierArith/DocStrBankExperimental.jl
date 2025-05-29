```
readncfile(fname,backend::Module=NCDatasets)
```

Read in a NetCDF file and return variables/dimensions as `NCvar` structs, and     file attributes as `Dict`. Large variables/dimensions are not loaded into     memory. This can use either `NCDatasets.jl` or `NetCDF.jl`
