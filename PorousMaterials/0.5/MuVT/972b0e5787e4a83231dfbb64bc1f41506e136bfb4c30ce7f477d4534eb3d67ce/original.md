```
filename = μVT_output_filename(xtal, molecule_templates, temperature, 
                               pressures, ljff, n_burn_cycles, 
                               n_sample_cycles; comment="", extension=".jld2")
```

This is the function that establishes the file naming convention used by [μVT_sim](@ref).

# Arguments

  * `xtal::Crystal`: porous xtal used in adsorption simulation
  * `molecule_templates::Array{Molecule, 1}`: template of the adsorbate molecules used in adsorption simulation
  * `temperature::Float64`:temperature of bulk gas phase in equilibrium with adsorbed phase in the porous material. units: Kelvin (K)
  * `pressures::Array{Float64, 1}`: partial pressures of bulk gas phase in equilibrium with adsorbed phase in the porous material. units: bar
  * `ljff::LJForceField`: the molecular model used in adsorption simulation
  * `n_burn_cycles::Int`: number of cycles to allow the system to reach equilibrium before sampling.
  * `n_sample_cycles::Int`: number of cycles used for sampling
  * `comment::String=""`: remarks to be included in the filename
  * `extension::String=".jld2"`: the file extension

# Returns

  * `filename::String`: the name of the specific `.jld2` simulation file
