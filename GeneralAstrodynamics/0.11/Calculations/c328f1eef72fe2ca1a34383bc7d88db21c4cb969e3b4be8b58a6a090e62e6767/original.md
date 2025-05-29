```julia
analyticalhalo(μ; Az, ϕ, steps, L, hemisphere)

```

Returns an analytical solution for a Halo orbit about `L`.

**Arguments:** 

  * `μ`: Non-dimensional mass parameter for the CR3BP system.
  * `Az`: Desired non-dimensional Z-amplitude for Halo orbit.
  * `ϕ`: Desired Halo orbit phase.
  * `steps`: Number of non-dimensional timepoints in returned state.
  * `L`: Lagrange point to orbit (L1 or L2).
  * `hemisphere`: Specifies northern or southern Halo orbit.

**Outputs:**

  * Synodic position vector `r::Array{<:AbstractFloat}`
  * Synodic velocity vector `v::Array{<:Abstractfloat}`.
  * Halo orbit period `Τ`.
  * Throws `ArgumentError` if L is not `1` or `2`.

**References:**

  * [Rund, 2018](https://digitalcommons.calpoly.edu/theses/1853/).
