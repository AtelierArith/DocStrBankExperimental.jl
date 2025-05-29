```
CMaterial(; kernel, model, zem, dmgmodel, maxdmg)
```

A material type used to assign the material of a [`Body`](@ref) with the local continuum consistent (correspondence) formulation of non-ordinary state-based peridynamics.

# Keywords

  * `kernel::Function`: Kernel function used for weighting the interactions between points. 
      (default: `linear_kernel`) 
      The following kernels can be used:

      * [`linear_kernel`](@ref)
      * [`cubic_b_spline_kernel`](@ref)
  * `model::AbstractConstitutiveModel`: Constitutive model defining the material behavior. 
      (default: `LinearElastic()`) 
      The following models can be used:

      * [`LinearElastic`](@ref)
      * [`NeoHooke`](@ref)
      * [`MooneyRivlin`](@ref)
      * [`SaintVenantKirchhoff`](@ref)
  * `zem::AbstractZEMStabilization`: Zero-energy mode stabilization. The   stabilization algorithm of Silling (2017) is used as default. 
      (default: [`ZEMSilling`](@ref))
  * `dmgmodel::AbstractDamageModel`: Damage model defining the damage behavior. 
      (default: [`CriticalStretch`](@ref))
  * `maxdmg::Float64`: Maximum value of damage a point is allowed to obtain. If this value is   exceeded, all bonds of that point are broken because the deformation gradient would then   possibly contain `NaN` values. 
      (default: `0.85`)

!!! note "Stability of fracture simulations"
    This formulation is known to be not suitable for fracture simulations without stabilization of the zero-energy modes. Therefore be careful when doing fracture simulations and try out different parameters for `maxdmg` and `zem`.


# Examples

```julia-repl
julia> mat = CMaterial()
CMaterial{LinearElastic, ZEMSilling, typeof(linear_kernel), CriticalStretch}(maxdmg=0.85)
```

---

```julia
CMaterial{CM,ZEM,K,DM}
```

Material type for the local continuum consistent (correspondence) formulation of non-ordinary state-based peridynamics.

# Type Parameters

  * `CM`: A constitutive model type. See the constructor docs for more informations.
  * `ZEM`: A zero-energy mode stabilization type. See the constructor docs for more        informations.
  * `K`: A kernel function type. See the constructor docs for more informations.
  * `DM`: A damage model type. See the constructor docs for more informations.

# Fields

  * `kernel::Function`: Kernel function used for weighting the interactions between points.   See the constructor docs for more informations.
  * `model::AbstractConstitutiveModel`: Constitutive model defining the material behavior. See   the constructor docs for more informations.
  * `zem::AbstractZEMStabilization`: Zero-energy mode stabilization. See the constructor docs   for more informations.
  * `dmgmodel::AbstractDamageModel`: Damage model defining the damage behavior. See the   constructor docs for more informations.
  * `maxdmg::Float64`: Maximum value of damage a point is allowed to obtain. See the   constructor docs for more informations.

# Allowed material parameters

When using [`material!`](@ref) on a [`Body`](@ref) with `CMaterial`, then the following parameters are allowed: Material parameters:

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

When specifying the `fields` keyword of [`Job`](@ref) for a [`Body`](@ref) with `CMaterial`, the following fields are allowed:

  * `position::Matrix{Float64}`: Position of each point.
  * `displacement::Matrix{Float64}`: Displacement of each point.
  * `velocity::Matrix{Float64}`: Velocity of each point.
  * `velocity_half::Matrix{Float64}`: Velocity parameter for Verlet time solver.
  * `acceleration::Matrix{Float64}`: Acceleration of each point.
  * `b_int::Matrix{Float64}`: Internal force density of each point.
  * `b_ext::Matrix{Float64}`: External force density of each point.
  * `damage::Vector{Float64}`: Damage of each point.
  * `n_active_bonds::Vector{Int}`: Number of intact bonds of each point.
  * `stress::Matrix{Float64}`: Stress tensor of each point.
  * `von_mises_stress::Vector{Float64}`: Von Mises stress of each point.
