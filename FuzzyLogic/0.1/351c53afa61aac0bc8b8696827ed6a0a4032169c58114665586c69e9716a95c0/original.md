```julia
struct LinearSugenoOutput{T} <: FuzzyLogic.AbstractSugenoOutputFunction
```

Represents an output variable that has a first-order polynomial relation on the inputs. Used for Sugeno inference systems.

  * `coeffs::Dictionaries.Dictionary{Symbol}`: coefficients associated with each input variable.
  * `offset::Any`: offset of the output.
