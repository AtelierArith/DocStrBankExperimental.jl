```
TransitParameters{T<:AbstractFloat} <: TransitOutput{T}
```

Transit times, impact parameters, sky-velocities, and derivatives.

# (User-facing) Fields

  * `ttbv::Matrix{T}` : The transit times, impact parameter, and sky-velocity of each body.
  * `dtbvdq0::Array{T,5}` : Derivatives of the transit times, impact parameters, and sky-velocities with respect to the initial Cartesian coordinates and masses.
  * `dtbvdelements::Array{T,5}` : Derivatives of the transit times, impact parameters, and sky-velocities with respect to the initial orbital elements and masses.
