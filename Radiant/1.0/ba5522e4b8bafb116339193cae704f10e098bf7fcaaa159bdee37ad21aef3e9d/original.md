```
Discrete_Ordinates
```

Structure used to define the discretization method associated with the transport of a particle.

# Mandatory field(s)

  * `particle::Particle` : particle for which the discretization methods is defined
  * `solver_type::String` : type of solver for the transport calculations.
  * `quadrature_type::String` : type of quadrature for the angular domain.
  * `quadrature_order::Int64` : order of the quadrature for the angular domain.
  * `legendre_order::Int64` : maximum order of the Legendre expansion for the differential cross-sections.
  * `scheme_type::Dict{String,String}` : type of schemes for the spatial or energy discretization.
  * `scheme_order::Dict{String,Int64}` : order of the expansion for the discretization schemes.

# Optional field(s) - with default values

  * `angular_fokker_planck::String = "finite-difference"` : type of discretization for the angular Fokker-Planck operation.
  * `angular_boltzmann::String = "galerkin-d"` : type of discretization for the Boltzmann operation.
  * `convergence_criterion::Float64 = 1e-7` : convergence criterion of in-group iterations.
  * `maximum_iteration::Int64 = 300` : maximum number of in-group iterations.
  * `acceleration::Int64 = "none"` : acceleration method for the in-group iterations.
