```julia
nc_agg(
    f::AbstractString;
    ...
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}
nc_agg(
    f::AbstractString,
    fout;
    by,
    fun,
    outdir,
    overwrite,
    verbose
) -> Union{Nothing, NCDatasets.NCDataset{Nothing, Missing}}

```

# Arguments

  * `f`: input file
  * `fout`: output file
  * `by`: "year" or "month", or a function to group dates

```julia
nc_agg(f; ...)
nc_agg(f, fout; by, fun, outdir, overwrite, verbose)
```

defined at [`packages/NetCDFTools/QX4TD/src/utilize/nc_agg.jl:15`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/utilize/nc_agg.jl).

# Examples

```
nc_agg(f, fout; by="year", fun=mean, outdir="./OUTPUT", overwrite=false, verbose=true)
```
