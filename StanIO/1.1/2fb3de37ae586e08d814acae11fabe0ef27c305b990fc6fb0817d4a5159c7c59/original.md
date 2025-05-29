Read .csv output files created by Stan's cmdstan executable.

```julia
read_csvfiles(
    csvfiles,
    output_format;
    include_internals,
    return_parameters,
    n_chains,
    n_samples,
    kwargs...
)

```

# Extended help

### Required arguments

```julia
* `csvfiles` : Vector of file names
* `output_format` : Requested output format
```

### Optional arguments

```julia
* `include_internals=true` : Include internal parameters in output_format
* `return_parameters=false` : Return parameters names as in .csv files
* `n_chains=length(csvfiles)` : No of chains
* `n_samples=1000`: No of samples
* `kwargs...`
```

Not exported
