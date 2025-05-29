```
SimulationSequence(
    models::SimulationModels,
    feedforward::Dict{String, Vector{<:AbstractAffectFeedforward}}
    ini_cond_chronology::InitialConditionChronology
)
```

Construct the simulation sequence between decision and emulation models.

# Arguments

  * `models::SimulationModels`: Vector of decisions and emulation models.
  * `feedforward = Dict{String, Vector{<:AbstractAffectFeedforward}}()`: Optional dictionary to specify how information and variables are exchanged between decision and emulation models.
  * `ini_cond_chronology::InitialConditionChronology =  InterProblemChronology()`: Define information sharing model between stages with [`InterProblemChronology`](@ref)

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
```
