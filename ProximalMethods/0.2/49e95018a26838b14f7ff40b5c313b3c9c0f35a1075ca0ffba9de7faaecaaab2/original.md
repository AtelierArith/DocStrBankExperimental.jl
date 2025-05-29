```
smooth(x, λ, f, ∇f!, y_prev)
```

Compute the proximal operator of a general smooth function `f` with in-place gradient `∇f!` and scaling parameter `λ` at `x` using L-BFGS. Warm starting is accomodated by the use of `y_prev`, the previous solution.

#### Arguments

  * `x::AbstractVector`     : input
  * `λ::Real`               : scaling parameter
  * `f::Function`           : objective function
  * `∇f!::Function`         : gradient
  * `y_prev::AbstractVector`: previous output

#### Returns

  * `y::AbstractVector` : output
