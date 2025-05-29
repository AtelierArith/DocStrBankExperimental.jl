```
IS_HS_PY(ϕ::T, k::T) where {T<:AbstractFloat}
```

Computes the inverse of the static structure factor 1/S(k) for hard spheres using the direct correlation function c(k) from the Percus-Yevick (PY) approximation. The inverse structure factor is given by 1/S(k) = 1 - n * c*tilde(q), where n is number density and c*tilde(q) is the FT of c(r). For PY hard spheres, this is often written as 1/S(k) = 1 - 24*ϕ*c*PY(k), where c*PY(k) is the dimensionless form computed by `C_HS_PY`.

# Arguments

  * `ϕ::T`: The volume fraction of spheres. Should be in the range `[0, 1)`.
  * `k::T`: The dimensionless wavevector, k = q*sigma.

# Returns

  * Value of the inverse static structure factor 1/S(k).

# References

[1] J. P. Hansen and I. McDonald. Theory of Simple Liquids. Academic, London, 1990.
