Convert the output file created by cmdstan to the shape of choice

```julia
convert_a3d(a3d_array, cnames, ; kwargs...)

```

### Method

```julia
convert_a3d(a3d_array, cnames; output_format=::Val{Symbol}, start=1)
```

### Required arguments

```julia
* `a3d_array::Array{Float64, 3},`      : Read in from output files created by cmdstan                                   
* `cnames::Vector{AbstractString}`     : Monitored variable names
```

### Optional arguments

```julia
* `::Val{Symbol}`                      : Output format, default is :mcmcchains
* `::start=1`                          : First draw for MCMCChains.Chains
```

### Return values

```julia
* `res`                       : Draws converted to the specified format.
```
