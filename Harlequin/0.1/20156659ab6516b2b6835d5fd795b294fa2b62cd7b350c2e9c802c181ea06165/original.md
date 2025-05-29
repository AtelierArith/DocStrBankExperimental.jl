```
mutable struct NobsMatrixElement
```

This structure encodes the condition matrix for a pixel in the map. It is essentially matrix M_p in Eq. (10) of KurkiSuonio2009, but with steroids, as it implements the following fields:

  * `m`: the 3×3 matrix in Eq. (10)
  * `invm`: the 3×3 inverse of `m`
  * `invcond`: the inverse of the condition number *rcond* for `m`; this field is useful to check whether the samples in a TOD and the attack angles are sufficient to constrain a unique solution for I, Q, and U for that pixel.
  * `neglected`: a Boolean flag telling whether the pixel was skipped or not during map-making (this usually happens if `invcond` is too small)

A typical use case is an array of `NobsMatrixElement` objects in an array that get updated via [`update_nobs_matrix!`](@ref), like in the following example:

```julia
NPIX = 10   # Number of pixels in the map
nobs_matrix = [NobsMatrixElement() for i in 1:NPIX]

# The variables psi_angle, sigma_squared, pixidx, and flagged
# must have been defined somewhere else; they contain the TOD
update_nobs_matrix!(nobs_matrix, psi_angle, sigma_squared, pixidx, flagged)
```
