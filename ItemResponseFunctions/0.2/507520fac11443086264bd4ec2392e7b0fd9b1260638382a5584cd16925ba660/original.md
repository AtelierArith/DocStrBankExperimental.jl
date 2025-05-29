```julia
derivative_theta(M, theta, beta; scoring_function)

```

Calculate the derivative of the item (category) response function with respect to `theta` of model `M` given item parameters `beta` for response `y`. Returns the primal value and the first derivative.

If `y` is omitted, returns probabilities and derivatives for all possible responses (see also [`derivative_theta!`](@ref)).
