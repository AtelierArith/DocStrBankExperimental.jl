```julia
mutable struct AssemblyPattern{APT<:GradientRobustMultiPhysics.AssemblyPatternType, T<:Real, AT<:ExtendableGrids.AssemblyType, Tv<:Real, Ti<:Integer, ActionType<:Union{GradientRobustMultiPhysics.AbstractAction, GradientRobustMultiPhysics.AbstractNonlinearFormHandler}}
```

each assembly pattern has one of the assembly pattern types (APT) that trigger different assemblies for the involved finite element spaces, operators and an assigned action. The assembly type (AT) determines if the assembly takes place on cells, faces or edges etc. (relatively to the assembly type of the first argument of the pattern)
