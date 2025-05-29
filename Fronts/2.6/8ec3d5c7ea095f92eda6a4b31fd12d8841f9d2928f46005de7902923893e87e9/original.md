```
InverseProblem(o, u[, weights; i, b, ob])
```

Problem type for inverse functions and parameter estimation with experimental data.

# Arguments

  * `o::AbstractVector`: values of the Boltzmann variable. See [`o`](@ref).
  * `u::AbstractVector`: observed solution values at each point in `o`.
  * `weights`: optional weights for the data.

# Keyword arguments

  * `i`: initial value, if known.
  * `b`: boundary value, if known.
  * `ob=0`: value of `o` at the boundary.

# See also

[`diffusivity`](@ref), [`sorptivity`](@ref), `Fronts.ParamEstim`
