```
shrinkage(x, λ, fac, b)
```

Compute the generalized shrinkage operator with scaling parameter `λ` at `x`, proximal operator of a quadratic function with quadratic parameters `A` and linear parameters `b` using a factorization `fac` of $I + λA$.

#### Arguments

  * `x::AbstractVector` : input
  * `λ::Real`           : scaling parameter
  * `fac::Factorization`: factorization of $I + λA$
  * `b::AbstractVector` : linear coefficients

#### Returns

  * `y::AbstractVector` : shrunken values
