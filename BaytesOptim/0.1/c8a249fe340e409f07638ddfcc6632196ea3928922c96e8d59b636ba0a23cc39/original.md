```julia
struct LBFGTune{R<:Real} <: BaytesCore.AbstractTune
```

Stores information used throughout optimization algorithms.

# Fields

  * `magnitude_penalty::Real`: Add `-0.5 * magnitude_penalty * sum(abs2, q)` to the log posterior **when finding the local optimum**. This can help avoid getting into high-density edge areas of the posterior which are otherwise not typical (eg multilevel models).

  * `iterations::Int64`: Maximum number of iterations in the optimization algorithm. Recall that we don't need to find the mode, or even a local mode, just be in a reasonable region.
