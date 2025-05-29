```julia
abstract type AbstractDEProblem <: SciMLBase.AbstractSciMLProblem
```

Base type for all DifferentialEquations.jl problems. Concrete subtypes of `AbstractDEProblem` contain the necessary information to fully define a differential equation of the corresponding type.
