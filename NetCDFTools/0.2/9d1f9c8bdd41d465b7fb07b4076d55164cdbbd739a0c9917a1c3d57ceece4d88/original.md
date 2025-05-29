```
open netcdf file, `nc_open` is alias of `NCDataset`
```

```julia
nc_open(
    f::Union{AbstractString, Vector{<:AbstractString}},
    args...;
    kwargs...
) -> Any

```

# Arguments

  * `mode`:

      * "a": append
      * "c": create

# Examples

```julia
nc_open(f, args; kwargs...)
```

defined at [`packages/NetCDFTools/QX4TD/src/nc_info.jl:20`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/nc_info.jl).

@seealso [NCDatasets.NCDataset()]
