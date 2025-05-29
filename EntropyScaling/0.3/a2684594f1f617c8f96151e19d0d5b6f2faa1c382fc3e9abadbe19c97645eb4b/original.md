```
FrameworkModel{T} <: AbstractEntropyScalingModel
```

Entropy scaling framework [schmitt*entropy*2024,schmitt*entropy*2025](@cite).

The entropy scaling framework provides a physical way to model transport properties  (viscosity, thermal conductivity, diffusion coeffficients) based on molecular-based EOS. It enables fitting new models using only few experimental data.

# Parameters

  * `α::Matrix{T}`: component-specific parameters (size: `5 x N_components`)

`m` (segment parameter of molecular-based EOS) and `Y₀⁺min` (minimum of the scaled  zero-density transport property) are additional internal parameters (not to be set at  construction).

# Constructors

  * `FrameworkModel(eos, params::Dict{P})`: Default constructor (see above).
  * `FrameworkModel(eos, datasets::Vector{TransportPropertyData}; opts::FitOptions=FitOptions(), solute=nothing)`:   Constructor for fitting new parameters `α` to experimental data (only applicable to pure components).   `datasets` contains the experimental data, see [`TransportPropertyData`](@ref).   `opts` enables controling the fitting procedure through [`FitOptions`](@ref).   `solute` is an EOS model of the solute (optional, for fitting diff. coeff. at infinite dilution).

# Example

```julia
using EntropyScaling, Clapeyron

# Load experimental sample data for n-butane
(T_exp,ϱ_exp,η_exp) = EntropyScaling.load_sample_data()
data = ViscosityData(T_exp, [], ϱ_exp, η_exp, :unknown)

# Create EOS model
eos_model = PCSAFT("butane")

# Create entropy scaling model (fit of parameters)
model = FrameworkModel(eos_model, [data])

# Calculation of the viscostiy at state
η = viscosity(model, 0.1e6, 300.)
```
