```
dataframe = isotherm_sim_results_to_dataframe(desired_props, xtal,
                                              molecule, temperature,
                                              pressures, ljff,
                                              n_burn_cycles, n_sample_cycles;
                                              where_are_jld_files=nothing)`
```

convert the `.jld2` results output files auto-saved from [`μVT_sim`](@ref) into a `DataFrame`. each row of the `DataFrame` corresponds to a pressure in the adsorption isotherm. `desired_props` is an array of desired properties from the results. to locate the requested output files, this function calls [`μVT_output_filename`](@ref) to retrieve the file names.

# Arguments

  * `desired_props::Array{String, 1}`: An array containing names of properties to be retrieved from the `.jld2` file
  * `xtal::Crystal`: The porous crystal
  * `molecule::Array{Molecule{Cart}, 1}`: The adsorbate molecule
  * `temperature::Float64`: The temperature in the simulation, units: Kelvin (K)
  * `pressures::Array{Array{Float64, 1}, 1}`: The pressures in the adsorption isotherm simulation(s), units: bar
  * `ljff::LJForceField`: The molecular model being used in the simulation to describe intermolecular Van der Waals interactions
  * `n_burn_cycles::Int64`: The number of burn cycles used in this simulation
  * `n_sample_cycles::Int64`: The number of sample cycles used in the simulations
  * `where_are_jld_files::Union{String, Nothing}=nothing`: The location to the simulation files. defaults to `PorousMaterials.rc[:paths][:simulations]`.
  * `comment::String=""`: comment appended to outputfilename

# Returns

  * `dataframe::DataFrame`: A `DataFrame` containing the simulated data along the adsorption isotherm, whose columns are for the specified properties

# Note

A range of pressures can be used to select a batch of simulation files to be included in the `DataFrame`.

# Example

```julia
xtal = Crystal("SBMOF-1.cif")
molecule = Molecule("Xe")
ljff = LJForceField("UFF"; mixing_rules="Lorentz-Berthelot")
temperature = 298.0 # K
pressures = 10 .^ range(-2; stop=2, length=15)

dataframe = isotherm_sim_results_to_dataframe(
    ["pressure (bar)", "⟨N⟩ (mmol/g)"],
    xtal,
    molecule,
    temperature,
    pressures,
    ljff,
    10000,
    10000
)
dataframe[Symbol("pressure (bar)")] # pressures
dataframe[Symbol("⟨N⟩ (mmol/g)")] # adsorption at corresponding pressures
```
