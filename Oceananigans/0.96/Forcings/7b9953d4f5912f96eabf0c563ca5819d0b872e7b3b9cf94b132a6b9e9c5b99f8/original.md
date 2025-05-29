```
AdvectiveForcing(u=ZeroField(), v=ZeroField(), w=ZeroField())
```

Build a forcing term representing advection by the velocity field `u, v, w` with an advection `scheme`.

# Example

# Using a tracer field to model sinking particles

```jldoctest
using Oceananigans

# Physical parameters
gravitational_acceleration          = 9.81     # m s⁻²
ocean_density                       = 1026     # kg m⁻³
mean_particle_density               = 2000     # kg m⁻³
mean_particle_radius                = 1e-3     # m
ocean_molecular_kinematic_viscosity = 1.05e-6  # m² s⁻¹

# Terminal velocity of a sphere in viscous flow
Δb = gravitational_acceleration * (mean_particle_density - ocean_density) / ocean_density
ν = ocean_molecular_kinematic_viscosity
R = mean_particle_radius

w_Stokes = - 2/9 * Δb / ν * R^2 # m s⁻¹

settling = AdvectiveForcing(w=w_Stokes)

# output
AdvectiveForcing:
├── u: ZeroField{Int64}
├── v: ZeroField{Int64}
└── w: ConstantField(-1.97096)
```
