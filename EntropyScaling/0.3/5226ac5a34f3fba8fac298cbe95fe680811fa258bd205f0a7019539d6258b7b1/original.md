```
RefpropRESModel{T} <: AbstractEntropyScalingModel
```

Entropy scaling model based on Refprop EOS [yang*linking*2022,yang*entropy*2021](@cite). 

A database provides ready-to-use models for the viscosity of several fluids. The model can favourably be used in combination with [`Clapeyron.jl`](https://github.com/ClapeyronThermo/Clapeyron.jl) and [`Coolprop.jl`](https://github.com/CoolProp/CoolProp.jl) (see examples).

# Parameters

  * `n::Matrix{T}`: component-specific *or* global (group) parameters
  * `ξ::Vector{T}`: component-specific scaling parameter in case global parameters are used (`ξ = 1` for individual fits)
  * `σ::Vector{T}`: LJ size parameter for the Chapman-Enskog model
  * `ε::Vector{T}`: LJ energy parameter for the Chapman-Enskog model
  * `crit::Dict{Symbol,Vector}`: parameters for critical contribution of thermal conductivity (keys: `:φ0`, `:Γ`, `:qD`, and `:Tref`)

# Constructors

  * `RefpropRESModel(eos, params::Dict{P})`: Default constructor (see above).
  * `RefpropRESModel(eos, components)`: Creates a ES model using the parameters provided in the database (recommended).    `RefpropRESModel(components)` creates the EOS model on-the-fly (only works if `Clapeyron.jl` and `Coolprop.jl` are loaded).

!!! info
    The default CoolProp EOS is used here which does not necessarily match the choice of the original papers.  This might lead to slight deviations to the values in the original papers (especially for the thermal conductivity).


# Example

```julia
using EntropyScaling, Clapeyron, CoolProp

model_pure = RefpropRESModel("R134a")
η_pure = viscosity(model_pure, 1e5, 300.; phase=:liquid)

model_mix = RefpropRESModel(["decane","butane"])
η_mix = viscosity(model_mix, 1e5, 300., [.5,.5])
```
