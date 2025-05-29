```
k_VW(ϕ_HS::T, k_HS::T) where {T<:AbstractFloat}
```

Computes the wave vector correction for hard spheres using the Verlet-Weiss (VW) approximation. This gives an effective wavevector k*eff. k*eff = k*HS * (ϕ*eff / ϕ_HS)^(1/3)

# Arguments

  * `ϕ_HS::T`: The original packing fraction of the hard-sphere system.
  * `k_HS::T`: The original (dimensionless) wave vector.

# Returns

  * `T`: The Verlet-Weiss corrected effective wave vector.

# References

[1] Loup Verlet and Jean-Jacques Weis. Phys. Rev. A 5, 939 – Published 1 February 1972.
