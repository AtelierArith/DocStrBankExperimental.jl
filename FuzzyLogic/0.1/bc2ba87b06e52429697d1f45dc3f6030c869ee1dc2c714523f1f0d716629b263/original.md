```julia
struct ConstantSugenoOutput{T<:Real} <: FuzzyLogic.AbstractSugenoOutputFunction
```

Represents constant output in Sugeno inference systems.

  * `c::Real`: value of the constant output.
