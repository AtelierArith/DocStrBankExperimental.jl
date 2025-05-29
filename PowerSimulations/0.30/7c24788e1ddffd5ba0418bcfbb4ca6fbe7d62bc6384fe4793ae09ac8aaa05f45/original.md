```
Simulation(
    sequence::SimulationSequence,
    name::String,
    steps::Int
    models::SimulationModels,
    simulation_folder::String,
    initial_time::Union{Nothing, Dates.DateTime}
)
```

Construct the `Simulation` structure to run the sequence of decision and emulation models specified.

# Arguments

  * `sequence::SimulationSequence`: Simulation sequence that specify how the decision and emulation models will be executed.
  * `name::String`: Name of the Simulation
  * `steps::Int`: Number of steps on which the sequence of models will be executed
  * `models::SimulationModels`: List of Decision and Emulation Models
  * `simulation_folder::String`: Folder on which results will be stored
  * `initial_time::Union{Nothing, Dates.DateTime} = nothing`: Initial time of which the simulation starts. If nothing it will default to the first timestamp of time series of the system.

# Example

```julia
template_uc = template_unit_commitment()
template_ed = template_economic_dispatch()
my_decision_model_uc = DecisionModel(template_1, sys_uc, optimizer, name = "UC")
my_decision_model_ed = DecisionModel(template_ed, sys_ed, optimizer, name = "ED")
models = SimulationModels(
    decision_models = [
        my_decision_model_uc,
        my_decision_model_ed
    ]
)
# The following sequence set the commitment variables (`OnVariable`) for `ThermalStandard` units from UC to ED.
sequence = SimulationSequence(;
    models = models,
    feedforwards = Dict(
        "ED" => [
            SemiContinuousFeedforward(;
                component_type = ThermalStandard,
                source = OnVariable,
                affected_values = [ActivePowerVariable],
            ),
        ],
    ),
)

sim = Simulation(
    sequence = sequence,
    name = "Sim",
    steps = 5,
    models = models,
    simulation_folder = mktempdir(cleanup=true),
)
```
