```julia
abstract type AbstractScalarILMProblem{DT, ST, DTP} <: ImmersedLayers.AbstractILMProblem{DT, ST, DTP}
```

When defining a problem type with scalar data, make it a subtype of this.
