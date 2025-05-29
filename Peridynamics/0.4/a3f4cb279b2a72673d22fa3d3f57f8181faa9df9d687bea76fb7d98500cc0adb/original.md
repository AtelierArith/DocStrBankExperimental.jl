```
material!(body, set_name; kwargs...)
material!(body; kwargs...)
```

Assign material point parameters to points of `body`. If no `set_name` is specified, then the parameters will be set for all points of the body.

# Arguments

  * `body::AbstractBody`: [`Body`](@ref).
  * `set_name::Symbol`: The name of a point set of this body.

# Keywords

Allowed keywords depend on the selected material model. Please look at the documentation of the material you specified when creating the body. The default material keywords are:

Material parameters:

  * `horizon::Float64`: Radius of point interactions.
  * `rho::Float64`: Density.

Elastic parameters:

  * `E::Float64`: Young's modulus.
  * `nu::Float64`: Poisson's ratio.
  * `G::Float64`: Shear modulus.
  * `K::Float64`: Bulk modulus.
  * `lambda::Float64`: 1st Lamé parameter.
  * `mu::Float64`: 2nd Lamé parameter.

Fracture parameters:

  * `Gc::Float64`: Critical energy release rate.
  * `epsilon_c::Float64`: Critical strain.

!!! note "Elastic parameters"
    Note that exactly two elastic parameters are required to specify a material.


!!! note "Fracture parameters"
    To enable fracture in a simulation, define one of the allowed fracture parameters. If none are defined, fracture is disabled.


# Throws

  * Error if a kwarg is not eligible for specification with the body material.

# Example

```julia-repl
julia> material!(body; horizon=3.0, E=2.1e5, rho=8e-6, Gc=2.7)

julia> body
1000-point Body{BBMaterial{NoCorrection}}:
  1 point set(s):
    1000-point set `all_points`
  1 point parameter(s):
    Parameters BBMaterial: δ=3.0, E=210000.0, nu=0.25, rho=8.0e-6, Gc=2.7
```
