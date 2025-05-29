```julia
nc_write!(
    f::AbstractString,
    varname::AbstractString,
    val,
    dims::Vector{<:Union{AbstractString, NetCDFTools.NcDim}};
    ...
) -> NCDatasets.NCDataset{Nothing, Missing}
nc_write!(
    f::AbstractString,
    varname::AbstractString,
    val,
    dims::Vector{<:Union{AbstractString, NetCDFTools.NcDim}},
    attrib::Dict;
    units,
    longname,
    compress,
    global_attrib,
    mode,
    kw...
) -> NCDatasets.NCDataset{Nothing, Missing}

```

```julia
nc_write!(f, varname, val, dims; ...)
nc_write!(
    f,
    varname,
    val,
    dims,
    attrib;
    units,
    longname,
    compress,
    global_attrib,
    mode,
    kw...
)
```

defined at [`packages/NetCDFTools/QX4TD/src/nc_write.jl:73`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/nc_write.jl).
