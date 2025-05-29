```
ElementsIC{T<:AbstractFloat} <: InitialConditions{T}
```

Initial conditions, specified by a hierarchy vector and orbital elements.

# Fields

  * `elements::Matrix{T}` : Masses and orbital elements.
  * `ϵ::Matrix{T}` : Matrix of Jacobi coordinates
  * `amat::Matrix{T}` : 'A' matrix from [Hamers and Portegies Zwart 2016](https://doi.org/10.1093/mnras/stw784).
  * `nbody::Int64` : Number of bodies.
  * `m::Vector{T}` : Masses of bodies.
  * `t0::T` : Initial time [Days].
