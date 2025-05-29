```
S_HS_PY(ϕ::T, k::T) where {T<:AbstractFloat}
```

Returns the Static Structure Factor S(k) for hard spheres under the Percus-Yevick (PY) Closure. The input `k` is expected to be the dimensionless wavevector k = q*sigma.

The formula used is: S(k) = 1 / (1 - 24*ϕ*c(k))

# Arguments

  * `ϕ::T`: The volume fraction. Should be in the range `[0, 1)`.
  * `k::T`: The dimensionless wavevector, k = q*sigma.

# Returns

  * Value of the static structure factor S(k).

# References

[1] J. P. Hansen and I. McDonald. Theory of Simple Liquids. Academic, London, 1990.
