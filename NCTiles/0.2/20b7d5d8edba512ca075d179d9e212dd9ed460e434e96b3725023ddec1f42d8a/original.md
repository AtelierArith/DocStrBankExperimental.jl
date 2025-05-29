```
NCData
```

Data structure containing a string or an array of strings (file names) of     NetCDF files as well as information needed to read a file.

```
struct NCData
    fname::AbstractString
    varname::AbstractString
    backend::Module
    precision::Type
end
```
