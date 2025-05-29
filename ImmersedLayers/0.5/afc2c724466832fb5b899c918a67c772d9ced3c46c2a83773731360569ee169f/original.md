```julia
abstract type AbstractVectorILMProblem{DT, ST, DTP} <: ImmersedLayers.AbstractILMProblem{DT, ST, DTP}
```

When defining a problem type with vector data, make it a subtype of this.
