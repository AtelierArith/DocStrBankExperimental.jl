```julia
abstract type Reconstruct{FETypeR, O} <: ??
```

reconstruction operator: evaluates a reconstructed version of the finite element function.

FETypeR specifies the reconstruction space (needs to be defined for the finite element that it is applied to). O specifies the StandardFunctionOperator that shall be evaluated.
