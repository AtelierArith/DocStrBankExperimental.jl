```julia
mutable struct HarmonicEquation
```

Holds a set of algebraic equations governing the harmonics of a `DifferentialEquation`.

# Fields

  * `equations::Vector{Symbolics.Equation}`: A set of equations governing the harmonics.
  * `variables::Vector{QuestBase.HarmonicVariable}`: A set of variables describing the harmonics.
  * `parameters::Vector{Symbolics.Num}`: The parameters of the equation set.
  * `natural_equation::QuestBase.DifferentialEquation`: The natural equation (before the harmonic ansatz was used).
  * `jacobian::Matrix{Symbolics.Num}`: The Jacobian of the natural equation.
