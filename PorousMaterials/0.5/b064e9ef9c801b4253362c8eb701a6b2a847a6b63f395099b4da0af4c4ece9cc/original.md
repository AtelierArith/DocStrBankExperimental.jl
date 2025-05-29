```
eparams = setup_Ewald_sum(box, sr_cutoff_r; ϵ=1e-6, verbose=false)
```

Given the short-range cutoff radius and simulation box, automatically compute Ewald convergence parameter and number of k-vector replications in Fourier space required for a given precision. Constructs and returns Ewald parameters data type with this information.

Also, pre-compute weights on k-vector contributions to Ewald sum in Fourier space.

Also, allocate OffsetArrays for storing e^{i * k ⋅ r} where r = x - xⱼ and k is a reciprocal lattice vector.

# Arguments

  * `box::Box`: the simulation box containing the reciprocal lattice.
  * `sr_cutoff_r::Float64`: cutoff-radius (units: Å) for short-range contributions to Ewald
  * `ϵ::Float64`: desired level of precision. Typical value is 1e-6, but this does not
  * `verbose::Bool`: If `true` will print results

# Returns

  * `eparams::EwaldParams`: data structure containing Ewald summation settings corresponding weights indicating the contribution to the Fourier sum.
