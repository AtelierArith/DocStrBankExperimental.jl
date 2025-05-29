```julia
get_decision_problem_results(
    results::PowerSimulations.SimulationResults,
    problem::String;
    populate_system,
    populate_units
) -> PowerSimulations.SimulationProblemResults{PowerSimulations.DecisionModelSimulationResults}

```

Return SimulationProblemResults corresponding to a SimulationResults

# Arguments

  * `sim_results::PSI.SimulationResults`: the simulation results to read from
  * `problem::String`: the name of the problem (e.g., "UC", "ED")
  * `populate_system::Bool = true`: whether to set the results' system as if using [`get_system!`](@ref)
  * `populate_units::Union{IS.UnitSystem, String, Nothing} = IS.UnitSystem.NATURAL_UNITS`: the units system with which to populate the results' system, if any (requires `populate_system=true`)
