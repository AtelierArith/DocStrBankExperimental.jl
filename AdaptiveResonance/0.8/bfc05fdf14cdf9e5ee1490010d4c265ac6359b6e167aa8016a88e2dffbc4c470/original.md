```julia
mutable struct opts_FAM <: AdaptiveResonance.ARTOpts
```

# Summary

Implements a Fuzzy ARTMAP learner's options.

These options are a [`Parameters.jl`](https://github.com/mauro3/Parameters.jl) struct, taking custom options keyword arguments. Each field has a default value listed below.

# Fields

  * `rho::Float64`: Vigilance parameter: rho ∈ [0, 1].  Default: 0.6
  * `alpha::Float64`: Choice parameter: alpha > 0.  Default: 1.0e-7
  * `epsilon::Float64`: Match tracking parameter: epsilon ∈ (0, 1).  Default: 0.001
  * `beta::Float64`: Learning parameter: beta ∈ (0, 1].  Default: 1.0
  * `max_epochs::Int64`: Maximum number of epochs during training: max_epochs ∈ [1, Inf)  Default: 1
  * `uncommitted::Bool`: Uncommitted node flag.  Default: true
  * `display::Bool`: Display flag for progress bars.  Default: false
  * `sort::Bool`: Flag to sort the F2 nodes by activation before the match phase

    When true, the F2 nodes are sorted by activation before match. When false, an iterative argmax and inhibition procedure is used to find the best-matching unit.  Default: false
