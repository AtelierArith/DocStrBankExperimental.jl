```
ProblemTemplate(::Type{T}) where {T<:PM.AbstractPowerFormulation}
```

Creates a model reference of the PowerSimulations Optimization Problem.

# Arguments

  * `model::Type{T<:PM.AbstractPowerFormulation}`:

# Example

template = ProblemTemplate(CopperPlatePowerModel)
