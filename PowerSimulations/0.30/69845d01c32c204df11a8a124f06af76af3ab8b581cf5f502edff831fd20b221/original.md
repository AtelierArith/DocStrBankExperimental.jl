```
SimulationModels(
    decision_models::Vector{<:DecisionModel},
    emulation_models::Union{Nothing, EmulationModel}
)
```

Stores the OperationProblem definitions to be used in the simulation. When creating the SimulationModels, the order in which the models are created determines the order on which the simulation is executed.

# Arguments

  * `decision_models::Vector{<:DecisionModel}`: Vector of decision models.
  * `emulation_models::Union{Nothing, EmulationModel}`: Optional argument to include

an EmulationModel in the Simulation

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
```
