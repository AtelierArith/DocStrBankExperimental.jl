```julia
load_results!(
    res::PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults},
    count::Int64;
    initial_time,
    variables,
    duals,
    parameters,
    aux_variables,
    expressions,
    store
)

```

Load the simulation results into memory for repeated reads. This is useful when loading results from remote locations over network connections, when reading the same data very many times, etc. Multiple calls augment the cache according to these rules, where "variable" means "variable, expression, etc.":

  * Requests for an already cached variable at a lesser `count` than already cached do *not* decrease the `count` of the cached variable
  * Requests for an already cached variable at a greater `count` than already cached *do* increase the `count` of the cached variable
  * Requests for new variables are fulfilled without evicting existing variables

Note that `count` is global across all variables, so increasing the `count` re-reads already cached variables. For each variable, each element must be the name encoded as a string, like `"ActivePowerVariable__ThermalStandard"` or a Tuple with its constituent types, like `(ActivePowerVariable, ThermalStandard)`. To clear the cache, use [`Base.empty!`](@ref).

# Arguments

  * `count::Int`: Number of windows to load.
  * `initial_time::Dates.DateTime` : Initial time of first window to load. Defaults to first.
  * `aux_variables::Vector{Union{String, Tuple}}`: Optional list of aux variables to load.
  * `duals::Vector{Union{String, Tuple}}`: Optional list of duals to load.
  * `expressions::Vector{Union{String, Tuple}}`: Optional list of expressions to load.
  * `parameters::Vector{Union{String, Tuple}}`: Optional list of parameters to load.
  * `variables::Vector{Union{String, Tuple}}`: Optional list of variables to load.
