```
TransitTiming{T<:AbstractFloat} <: TransitOutput{T}
```

Transit times and derivatives.

# (User-facing) Fields

  * `tt::Matrix{T}` : The transit times of each body.
  * `dtdq0::Array{T,4}` : Derivatives of the transit times with respect to the initial Cartesian coordinates and masses.
  * `dtdelements::Array{T,4}` : Derivatives of the transit times with respect to the initial orbital elements and masses.
