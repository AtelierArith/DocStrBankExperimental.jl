```
NCvar
```

Data structure containing information needed to write a variable to NetCDF files. 

Instead of loading the data into memory, one can provide a list of input file names (see `Bindata`).

Attributes (`atts`) : 1. string attributes will be writen to netcdf files; 2. a function attribute  called "readdata"NCTiles.readata will be used instead of the `NCTiles.readata` default.

```
struct NCvar
    name::String
    units::String
    dims
    values
    atts::Union{Dict,Nothing}
    backend::Module
end
```
