```
build!(rng, genealogy; kwargs...)
```

Build a genealogy.

# Methods

```julia
build!(rng, arg; winwidth, buffer, noprogress)
```

defined at [`packages/Moonshine/7JVTP/src/Arg/Recombination.jl:681`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Arg/Recombination.jl).

```julia
build!(rng, tree; Dist, bias0, threshold_prop)
```

defined at [`packages/Moonshine/7JVTP/src/Tree.jl:243`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/Tree.jl).

# Arguments

  * `winwidth` (`∞`): width of the window of positions to consider
  * `noprogress` (`false`): hide progress bar
  * `Dist` (`Hamming{Int}()`): distance used to compute coalescence probabilities
  * `bias0` (`10`): distance multiplier: higher values favour coalescence events between similar haplotypes
  * `threshold_prop` (`1`): proportion of events to consider when sampling
