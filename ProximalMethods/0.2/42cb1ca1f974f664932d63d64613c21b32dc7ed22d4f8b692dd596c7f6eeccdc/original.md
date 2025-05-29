```
shrinkage(x, λ, A, b)
```

Compute the generalized shrinkage operator with scaling parameter `λ` at `x`, proximal operator of a quadratic function with quadratic parameters `A` and linear parameters `b`.

#### Arguments

  * `x::AbstractVector` : input
  * `λ::Real`           : scaling parameter
  * `A::AbstractMatrix` : quadratic coefficients
  * `b::AbstractVector` : linear coefficients

#### Returns

  * `y::AbstractVector` : shrunken values
