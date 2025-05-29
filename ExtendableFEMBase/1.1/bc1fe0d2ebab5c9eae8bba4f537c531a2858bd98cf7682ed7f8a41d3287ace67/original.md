```julia
abstract type SymmetricGradient{offdiagval} <: ??
```

evaluates the symmetric part of the gradient of the finite element function and returns its Voigt compression (off-diagonals on position [j,k] and [k,j] are added together and weighted with offdiagval).
