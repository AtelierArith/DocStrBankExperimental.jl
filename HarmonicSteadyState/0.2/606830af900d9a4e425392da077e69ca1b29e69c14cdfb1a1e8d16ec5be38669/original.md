```
Polyhedral
```

The Polyhedral homotopy method constructs a homotopy based on the polyhedral structure of the polynomial system. It is more efficient than the Total Degree method for sparse systems, meaning most of the coefficients are zero. It can be especially useful if you don't need to find the zero solutions (`only_non_zero = true`), resulting in a speed up. See [HomotopyContinuation.jl](https://www.juliahomotopycontinuation.org/guides/polyhedral/) for more information.

# Fields

  * `only_non_zero::Bool`: Boolean indicating if only non-zero solutions are considered.
  * `thread::Bool`: Boolean indicating if threading is enabled.
  * `tracker_options::HomotopyContinuation.TrackerOptions`: Options for the tracker.
  * `endgame_options::HomotopyContinuation.EndgameOptions`: Options for the endgame.
  * `compile::Union{Bool, Symbol}`: Compilation options.
  * `seed::UInt32`: Seed for random number generation.
