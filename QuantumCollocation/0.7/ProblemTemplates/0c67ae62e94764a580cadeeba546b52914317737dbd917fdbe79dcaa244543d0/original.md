```
QuantumStateMinimumTimeProblem(traj, sys, obj, integrators, constraints; kwargs...)
QuantumStateMinimumTimeProblem(prob; kwargs...)
```

Construct a `DirectTrajOptProblem` for the minimum time problem of reaching a target state.

# Keyword Arguments

  * `state_name::Symbol=:ψ̃`: The symbol for the state variables.
  * `final_fidelity::Union{Real, Nothing}=nothing`: The final fidelity.
  * `D=1.0`: The cost weight on the time.
  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: The Piccolo options.
