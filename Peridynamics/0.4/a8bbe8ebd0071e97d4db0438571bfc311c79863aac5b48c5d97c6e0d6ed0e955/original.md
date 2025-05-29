```
CKIMaterial(; dmgmodel)
```

A material type used to assign the material of a [`Body`](@ref) with the continuum-kinematics-inspired peridynamics formulation.

# Keywords

  * `dmgmodel::AbstractDamageModel`: Damage model defining the damage behavior. 
      (default: `CriticalStretch()`)

# Examples

```julia-repl
julia> mat = CKIMaterial()
CKIMaterial(dmgmodel=CriticalStretch())
```

---

```julia
CKIMaterial{DM}
```

Material type for the continuum-kinematics-inspired peridynamics framework.

# Type Parameters

  * `DM`: A damage model type. See the constructor docs for more informations.

# Fields

  * `dmgmodel::AbstractDamageModel`: Damage model defining the damage behavior. See the   constructor docs for more informations.

# Allowed material parameters

When using [`material!`](@ref) on a [`Body`](@ref) with `CKIMaterial`, then the following parameters are allowed: Material parameters:

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

Interaction parameters:

  * `C1::Float64`: One-neighbor interaction parameter. (default: `0.0`)
  * `C2::Float64`: Two-neighbor interaction parameter. (default: `0.0`)
  * `C3::Float64`: Two-neighbor interaction parameter. (default: `0.0`)

!!! warning "Specification of interaction parameters"
    If any of the interaction parameters is used with [`material!`](@ref), the Young's modulus and Poisson's ratio are ignored and only the specified interaction parameters will influence the force density calculated from that interaction.

    If no interaction parameter is specified, then the Young's modulus and Poisson's ratio are used to calculate these parameters accordingly to Ekiz, Steinmann, and Javili (2022).


!!! note "Elastic parameters"
    Note that exactly two elastic parameters are required to specify a material. Please choose two out of the six allowed elastic parameters.


# Allowed export fields

When specifying the `fields` keyword of [`Job`](@ref) for a [`Body`](@ref) with `CKIMaterial`, the following fields are allowed:

  * `position::Matrix{Float64}`: Position of each point.
  * `displacement::Matrix{Float64}`: Displacement of each point.
  * `velocity::Matrix{Float64}`: Velocity of each point.
  * `velocity_half::Matrix{Float64}`: Velocity parameter for Verlet time solver.
  * `acceleration::Matrix{Float64}`: Acceleration of each point.
  * `b_int::Matrix{Float64}`: Internal force density of each point.
  * `b_ext::Matrix{Float64}`: External force density of each point.
  * `damage::Vector{Float64}`: Damage of each point.
  * `n_active_one_nis::Vector{Int}`: Number of intact one-neighbor interactions of each point.
