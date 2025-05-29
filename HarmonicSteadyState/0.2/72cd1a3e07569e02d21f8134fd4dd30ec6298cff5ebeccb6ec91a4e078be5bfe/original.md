```
TotalDegree
```

The Total Degree homotopy method performs a homotopy $H(x, t) = γ t G(x) + (1-t) F(x)$ from the trivial polynomial system $F(x) =xᵢ^{dᵢ} +aᵢ$ with the maximal degree $dᵢ$ determined by the [Bezout bound](https://en.wikipedia.org/wiki/B%C3%A9zout%27s_theorem). The method guarantees to find all solutions, however, it comes with a high computational cost. See [HomotopyContinuation.jl](https://www.juliahomotopycontinuation.org/guides/totaldegree/) for more information.

# Fields

  * `gamma::Complex`: Complex multiplying factor of the start system G(x) for the homotopy
  * `thread::Bool`: Boolean indicating if threading is enabled.
  * `tracker_options::HomotopyContinuation.TrackerOptions`: Options for the tracker.
  * `endgame_options::HomotopyContinuation.EndgameOptions`: Options for the endgame.
  * `compile::Union{Bool, Symbol}`: Compilation options.
  * `seed::UInt32`: Seed for random number generation.
