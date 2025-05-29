```julia
second_derivative_theta!(
    M,
    probs,
    derivs,
    derivs2,
    theta,
    beta;
    scoring_function
)

```

Calculate the second derivative of the item (category) response function with respect to `theta` of model `M` given item parameters `beta` for response `y`. Returns the primal value, the first derivative, and the second derivative

If `y` is omitted, returns values and derivatives for all possible responses.

This function overwrites `probs`, `derivs` and `derivs2` with the respective values.
