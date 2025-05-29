```
struct ExpMethodGeneric{T}
ExpMethodGeneric()=ExpMethodGeneric{Val{13}}();
```

Generic exponential implementation of the method `ExpMethodHigham2005`, for any exp argument `x`  for which the functions `LinearAlgebra.opnorm`, `+`, `*`, `^`, and `/` (including addition with UniformScaling objects) are defined. The type `T` is used to adjust the number of terms used in the Pade approximants at compile time.

See "The Scaling and Squaring Method for the Matrix Exponential Revisited" by Higham, Nicholas J. in 2005 for algorithm details.
