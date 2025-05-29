```
OSBMaterial(; kernel, dmgmodel)
OSBMaterial{Correction}(; kernel, dmgmodel)
```

A material type used to assign the material of a [`Body`](@ref) with the ordinary state-based formulation of peridynamics.

Possible correction methods are:

  * [`NoCorrection`](@ref): No correction is applied. (default)
  * [`EnergySurfaceCorrection`](@ref): The energy based surface correction method of   Le and Bobaru (2018) is applied.

# Keywords

  * `kernel::Function`: Kernel function used for weighting the interactions between points. 
      (default: `linear_kernel`)
  * `dmgmodel::AbstractDamageModel`: Damage model defining the damage behavior. 
      (default: `CriticalStretch()`)

# Examples

```julia-repl
julia> mat = OSBMaterial()
OSBMaterial{NoCorrection}(dmgmodel=CriticalStretch())

julia> mat = OSBMaterial{EnergySurfaceCorrection}()
OSBMaterial{EnergySurfaceCorrection}(dmgmodel=CriticalStretch())
```

---

```julia
OSBMaterial{Correction,K,DM}
```

Material type for the ordinary state-based peridynamics formulation.

# Type Parameters

  * `Correction`: A correction algorithm type. See the constructor docs for more informations.
  * `K`: A kernel function type. See the constructor docs for more informations.
  * `DM`: A damage model type. See the constructor docs for more informations.

# Fields

  * `kernel::Function`: Kernel function used for weighting the interactions between points.
  * `dmgmodel::AbstractDamageModel`: Damage model defining the damage behavior. See the   constructor docs for more informations.

# Allowed material parameters

When using [`material!`](@ref) on a [`Body`](@ref) with `OSBMaterial`, then the following parameters are allowed: Material parameters:

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
    Note that exactly two elastic parameters are required to specify a material. Please choose two out of the six allowed elastic parameters.


# Allowed export fields

When specifying the `fields` keyword of [`Job`](@ref) for a [`Body`](@ref) with `OSBMaterial`, the following fields are allowed:

  * `position::Matrix{Float64}`: Position of each point.
  * `displacement::Matrix{Float64}`: Displacement of each point.
  * `velocity::Matrix{Float64}`: Velocity of each point.
  * `velocity_half::Matrix{Float64}`: Velocity parameter for Verlet time solver.
  * `acceleration::Matrix{Float64}`: Acceleration of each point.
  * `b_int::Matrix{Float64}`: Internal force density of each point.
  * `b_ext::Matrix{Float64}`: External force density of each point.
  * `damage::Vector{Float64}`: Damage of each point.
  * `n_active_bonds::Vector{Int}`: Number of intact bonds of each point.
