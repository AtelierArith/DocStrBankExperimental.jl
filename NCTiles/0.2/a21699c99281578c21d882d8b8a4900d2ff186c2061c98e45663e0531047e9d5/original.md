```
BinData
```

Data structure containing a string or an array of strings (NetCDF     file names) as well as metadata needed to read a file.

```
struct BinData
    fnames::Union{Array{String},String}
    precision::Type
    iosize::Tuple
    fldidx::Int
end
```
