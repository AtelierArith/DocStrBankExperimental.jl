```julia
load_results!(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.EmulationModelSimulationResults};
    aux_variables,
    duals,
    expressions,
    parameters,
    variables
)

```

Load the simulation results into memory for repeated reads. This is useful when loading results from remote locations over network connections.

For each variable/parameter/dual, etc., each element must be the name encoded as a string, like `"ActivePowerVariable__ThermalStandard"``or a Tuple with its constituent types, like`(ActivePowerVariable, ThermalStandard)`.

# Arguments

  * `aux_variables::Vector{Union{String, Tuple}}`: Optional list of aux variables to load.
  * `duals::Vector{Union{String, Tuple}}`: Optional list of duals to load.
  * `expressions::Vector{Union{String, Tuple}}`: Optional list of expressions to load.
  * `parameters::Vector{Union{String, Tuple}}`: Optional list of parameters to load.
  * `variables::Vector{Union{String, Tuple}}`: Optional list of variables to load.
