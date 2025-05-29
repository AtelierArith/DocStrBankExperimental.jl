```julia
build!(
    model::PowerSimulations.DecisionModel;
    output_dir,
    recorders,
    console_level,
    file_level,
    disable_timer_outputs
)

```

Build the Decision Model based on the specified DecisionProblem.

# Arguments

  * `model::DecisionModel{<:DecisionProblem}`: DecisionModel object
  * `output_dir::String`: Output directory for results
  * `recorders::Vector{Symbol} = []`: recorder names to register
  * `console_level = Logging.Error`:
  * `file_level = Logging.Info`:
  * `disable_timer_outputs = false` : Enable/Disable timing outputs
