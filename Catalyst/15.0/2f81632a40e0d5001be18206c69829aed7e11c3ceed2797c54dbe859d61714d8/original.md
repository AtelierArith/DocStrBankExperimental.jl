```julia
struct JumpInputs{S<:ModelingToolkit.JumpSystem, T<:SciMLBase.AbstractODEProblem}
```

Inputs for a JumpProblem from a given `ReactionSystem`.

# Fields

  * `sys`: The `JumpSystem` to define the problem over
  * `prob`: The problem the JumpProblem should be defined over, for example DiscreteProblem
