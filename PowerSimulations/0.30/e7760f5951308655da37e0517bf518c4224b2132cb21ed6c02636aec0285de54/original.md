```julia
Simulation(directory::AbstractString, model_info::Dict)

```

Constructs Simulation from a serialized directory. Callers should pass any kwargs here that they passed to the original Simulation.

# Arguments

  * `directory::AbstractString`: the directory returned from the call to serialize
  * `model_info::Dict`: Two-level dictionary containing model parameters that cannot be serialized. The outer dict should be keyed by the problem name. The inner dict must contain 'optimizer' and may contain 'jump_model'. These should be the same values used for the original simulation.
