```julia
mutable struct opts_SFAM <: AdaptiveResonance.ARTOpts
```

# Summary

Implements a Simple Fuzzy ARTMAP learner's options.

These options are a [`Parameters.jl`](https://github.com/mauro3/Parameters.jl) struct, taking custom options keyword arguments. Each field has a default value listed below.

# Fields

  * `rho::Float64`: Vigilance parameter: rho ∈ [0, 1].  Default: 0.75
  * `alpha::Float64`: Choice parameter: alpha > 0.  Default: 1.0e-7
  * `epsilon::Float64`: Match tracking parameter: epsilon ∈ (0, 1).  Default: 0.001
  * `beta::Float64`: Learning parameter: beta ∈ (0, 1].  Default: 1.0
  * `max_epoch::Int64`: Maximum number of epochs during training: max_epoch ∈ [1, Inf).  Default: 1
  * `display::Bool`: Display flag for progress bars.  Default: false
  * `uncommitted::Bool`: Flag to use an uncommitted node when learning.

    If true, new weights are created with ones(dim) and learn on the complement-coded sample. If false, fast-committing is used where the new weight is simply the complement-coded sample.  Default: false
  * `match::Symbol`: Selected match function.  Default: :basic_match
  * `activation::Symbol`: Selected activation function.  Default: :basic_activation
  * `update::Symbol`: Selected weight update function.  Default: :basic_update
  * `sort::Bool`: Flag to sort the F2 nodes by activation before the match phase

    When true, the F2 nodes are sorted by activation before match. When false, an iterative argmax and inhibition procedure is used to find the best-matching unit.  Default: false
