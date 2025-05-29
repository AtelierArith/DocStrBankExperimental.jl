```julia
sample_array(pt)

```

Copy the target chain(s) samples into an array with axes:  `iteration x variable x target chain`.  For example, with [`StabilizedPT`](@ref) there  are two target chains.  By default, there is only one chain produced. 

See [`extract_sample()`](@ref) for information how the variables are  flattened, and use [`sample_names()`](@ref) to obtain string  names for the flattened variables. 

The combination of this function and [`sample_names()`](@ref) is useful for  creating [MCMCChains](https://turinglang.org/MCMCChains.jl/stable/getting-started/)  which can then be used to obtain summary statistics, diagnostics, create trace plots,  and pair plots (via [PairPlots](https://sefffal.github.io/PairPlots.jl/dev/chains/)).
