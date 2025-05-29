```
kvectors = precompute_kvec_wts(kreps, box, α, max_mag_k_sqrd=Inf)
```

For speed, pre-compute the weights for each reciprocal lattice vector for the Ewald sum in Fourier space. This function takes advantage of the symmetry: cos(-k⋅(x-xᵢ)) + cos(k⋅(x-xᵢ)) = 2 cos(k⋅(x-xᵢ))

If `max_mag_k_sqrd` is passed, k-vectors with a magnitude greater than `max_mag_k_sqrd` are not included.

# Arguments

  * `kreps::Tuple{Int, Int, Int}`: number of k-vector replications required in a, b, c
  * `box::Box`: the simulation box containing the reciprocal lattice.
  * `α::Float64`: Ewald sum convergence parameter (units: inverse Å)
  * `max_mag_k_sqrd::Float64`: cutoff for |k|² in Fourier sum; if passed, do not include k-vectors with magnitude squared greater than this.

# Returns

  * `kvectors::Array{Kvector, 1}`: array of k-vectors to include in the Fourier sum and their corresponding weights indicating the contribution to the Fourier sum.
