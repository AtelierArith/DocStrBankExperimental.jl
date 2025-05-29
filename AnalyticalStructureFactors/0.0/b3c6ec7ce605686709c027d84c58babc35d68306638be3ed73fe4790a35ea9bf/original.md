```
C_HS_PY(ϕ::T, k::T) where {T<:AbstractFloat}
```

Computes the dimensionless direct correlation function c(k*sigma) for hard spheres using the Percus-Yevick (PY) approximation. The result is c(q*sigma), where q is the wavevector magnitude and sigma is the particle diameter. The input `k` is expected to be the dimensionless wavevector k = q*sigma.

# Arguments

  * `ϕ::T`: The volume fraction of spheres. Should be in the range `[0, 1)`.
  * `k::T`: The dimensionless wavevector, k = q*sigma, where q is the wavevector and sigma is the sphere diameter.

# Returns

  * Value of the direct correlation function c(k).

# References

[1] J. P. Hansen and I. McDonald. Theory of Simple Liquids. Academic, London, 1990.
