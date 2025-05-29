```
BBMaterial()
BBMaterial{Correction}()
```

A material type used to assign the material of a [`Body`](@ref) with the standard bond-based formulation of peridynamics.

# Keywords

  * `dmgmodel::AbstractDamageModel`: Damage model defining the fracture behavior.   (default: `CriticalStretch()`)

Possible correction methods are:

  * [`NoCorrection`](@ref): No correction is applied. (default)
  * [`EnergySurfaceCorrection`](@ref): The energy based surface correction method of   Le and Bobaru (2018) is applied.

# Examples

```julia-repl
julia> mat = BBMaterial()
BBMaterial{NoCorrection}()

julia> mat = BBMaterial{EnergySurfaceCorrection}()
BBMaterial{EnergySurfaceCorrection}()
```

---

```julia
BBMaterial{Correction}
```

Material type for the bond-based peridynamics formulation.

# Type Parameters

  * `Correction`: A correction algorithm type. See the constructor docs for more informations.
  * `DM`: A damage model type.

# Allowed material parameters

When using [`material!`](@ref) on a [`Body`](@ref) with `BBMaterial`, then the following parameters are allowed: Material parameters:

  * `horizon::Float64`: Radius of point interactions.
  * `rho::Float64`: Density.

Elastic parameters

  * `E::Float64`: Young's modulus.
  * `G::Float64`: Shear modulus.
  * `K::Float64`: Bulk modulus.
  * `lambda::Float64`: 1st Lamé parameter.
  * `mu::Float64`: 2nd Lamé parameter.

Fracture parameters:

  * `Gc::Float64`: Critical energy release rate.
  * `epsilon_c::Float64`: Critical strain.

!!! note "Poisson's ratio and bond-based peridynamics"
    In bond-based peridynamics, the Poisson's ratio is limited to 1/4 for 3D simulations. Therefore, only one additional elastic parameter is required. Optionally, the specification of a second keyword is allowed, if the parameter combination results in `nu = 1/4`.


# Allowed export fields

When specifying the `fields` keyword of [`Job`](@ref) for a [`Body`](@ref) with `BBMaterial`, the following fields are allowed:

  * `position::Matrix{Float64}`: Position of each point.
  * `displacement::Matrix{Float64}`: Displacement of each point.
  * `velocity::Matrix{Float64}`: Velocity of each point.
  * `velocity_half::Matrix{Float64}`: Velocity parameter for Verlet time solver.
  * `acceleration::Matrix{Float64}`: Acceleration of each point.
  * `b_int::Matrix{Float64}`: Internal force density of each point.
  * `b_ext::Matrix{Float64}`: External force density of each point.
  * `damage::Vector{Float64}`: Damage of each point.
  * `n_active_bonds::Vector{Int}`: Number of intact bonds of each point.
