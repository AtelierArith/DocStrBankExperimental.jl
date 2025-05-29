```
ChapmanEnskogModel <: AbstractTransportPropertyModel
```

Chapman-Enskog transport properties for the zero-density limit.

# Fields

  * `σ::Vector{T}`: Lennard-Jones size parameter (`[σ] = m`)
  * `ε::Vector{T}`: Lennard-Jones energy parameter (`[ε] = J`)
  * `Mw::Vector{T}`: molar mass (`[Mw] = kg mol⁻¹`)
  * `collision::C`: collision integral method (`KimMonroe()` (default) or `Neufeld()`, see [`Ω`](@ref))

# Constructors

  * `ChapmanEnskogModel(components; collision_integral=KimMonroe(), ref="", ref_id="")`: database constructor
  * `ChapmanEnskogModel(components, σ, ε, Mw; collision_integral=KimMonroe())`: custom parameters constructor

Input arguments can either be single values (pure) or vectors. The keywords `ref` (short reference) and `ref_id` (DOI or ISBN) enable the specification of the reference. Currently, parameters from [poling*properties*2001](@citet) and [yang*linking*2022](@citet) are in the database. Mixture properties are calculated according to the models from [wilke*viscosity*1950](@citet) (viscosity), [mason*approximate*1958](@citet) (thermal conductivity), and [miller*self-diffusion*1961](@citet) (self-diffusion).

# Example

```julia
using EntropyScaling 

# Construction with custom parameters
σ, ε, Mw = 3.758e-10, 148.6*EntropyScaling.kB, 16.043e-3            # from Poling et al.
model_methane = ChapmanEnskogModel("methane",σ,ε,Mw)

η_mix = viscosity(model_methane, NaN, 300.)
D_mix = self_diffusion_coefficient(model_methane, NaN, 300.)

# Construction from database
model_mix = ChapmanEnskogModel(["butane","methanol"]; ref="Poling et al. (2001)")

η_mix = viscosity(model_mix, NaN, 300., [.5,.5])
D_mix = self_diffusion_coefficient(model_mix, NaN, 300., [.5,.5])  
```
