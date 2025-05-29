```julia
abstract type SymmetricHessian{offdiagval} <: ??
```

evaluates only the symmetric part of the Hessian of some (possibly vector-valued) finite element function. A concatenation of Voigt compressed Hessians for each component of the finite element functions is returned. The weighting of the mixed derivatives can be steered with offdiagval (e.g. √2 or 1 depending on the use case).
