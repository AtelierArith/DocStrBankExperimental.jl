```julia
TikTak(quasirandom_N; keep_ratio, θ_min, θ_max, θ_pow)

```

The “TikTak” multistart method, as described in *Arnoud, Guvenen, and Kleineberg (2019)*.

This implements the *multistart* part, can be called with arbitrary local methods, see [`multistart_minimization`](@ref).

# Arguments

  * `quasirandom_N`: the number of quasirandom points for the first pass (using a Sobol sequence).

# Keyword arguments

  * `keep_ratio`: the fraction of best quasirandom points which are kept
  * `θ_min` and `θ_max` clamp the weight parameter, `θ_pow` determines the power it is raised to.

The defaults are from the paper cited above.
