```julia
derivative_theta!(
    M,
    probs,
    derivs,
    theta,
    beta;
    scoring_function
)

```

Calculate the derivative of the item (category) response function with respect to `theta` of model `M` given item parameters `beta` for all possible responses. This function overwrites `probs` and `derivs` with the item category response probabilities and derivatives respectively.
