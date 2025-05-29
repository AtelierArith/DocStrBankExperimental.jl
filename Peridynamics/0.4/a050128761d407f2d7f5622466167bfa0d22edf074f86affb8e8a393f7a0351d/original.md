```
BACMaterial(; kernel, model, dmgmodel, maxdmg)
```

A material type used to assign the material of a [`Body`](@ref) with the bond-associated correspondence formulation of Chen and Spencer (2019).

# Keywords

  * `kernel::Function`: Kernel function used for weighting the interactions between points.   (default: `linear_kernel`)
  * `model::AbstractConstitutiveModel`: Constitutive model defining the material behavior.   (default: `LinearElastic()`)
  * `dmgmodel::AbstractDamageModel`: Damage model defining the fracture behavior.   (default: `CriticalStretch()`)
  * `maxdmg::Float64`: Maximum value of damage a point is allowed to obtain. If this value is   exceeded, all bonds of that point are broken because the deformation gradient would then   possibly contain `NaN` values.   (default: `0.85`)

# Examples

```julia-repl
julia> mat = BACMaterial()
BACMaterial{LinearElastic, typeof(linear_kernel), CriticalStretch}()
```

---

```julia
BACMaterial{CM,K,DM}
```

Material type for the bond-associated correspondence formulation of Chen and Spencer (2019).

# Type Parameters

  * `CM`: A constitutive model type. See the constructor docs for more informations.
  * `K`: A kernel function type. See the constructor docs for more informations.
  * `DM`: A damage model type.

# Fields

  * `kernel::Function`: Kernel function used for weighting the interactions between points.
  * `model::AbstractConstitutiveModel`: Constitutive model defining the material behavior.
  * `dmgmodel::AbstractDamageModel`: Damage model defining the fracture behavior.
  * `maxdmg::Float64`: Maximum value of damage a point is allowed to obtain. See the   constructor docs for more informations.

# Allowed material parameters

When using [`material!`](@ref) on a [`Body`](@ref) with `BACMaterial`, then the following parameters are allowed:

  * `horizon::Float64`: Radius of point interactions.
  * `rho::Float64`: Density.
  * `E::Float64`: Young's modulus.
  * `nu::Float64`: Poisson's ratio.
  * `Gc::Float64`: Critical energy release rate.
  * `epsilon_c::Float64`: Critical strain.

# Allowed export fields

When specifying the `fields` keyword of [`Job`](@ref) for a [`Body`](@ref) with `BACMaterial`, the following fields are allowed:

  * `position::Matrix{Float64}`: Position of each point.
  * `displacement::Matrix{Float64}`: Displacement of each point.
  * `velocity::Matrix{Float64}`: Velocity of each point.
  * `velocity_half::Matrix{Float64}`: Velocity parameter for Verlet time solver.
  * `acceleration::Matrix{Float64}`: Acceleration of each point.
  * `b_int::Matrix{Float64}`: Internal force density of each point.
  * `b_ext::Matrix{Float64}`: External force density of each point.
  * `damage::Vector{Float64}`: Damage of each point.
  * `n_active_bonds::Vector{Int}`: Number of intact bonds of each point.
