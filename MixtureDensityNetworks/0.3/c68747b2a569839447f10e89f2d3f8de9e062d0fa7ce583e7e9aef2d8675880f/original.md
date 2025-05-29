```julia
predict_mode(
    m::MixtureDensityNetworks.MixtureDensityNetwork,
    X::Matrix{<:Real}
) -> Any

```

Predict the point associated with the highest probability in the conditional distribution P(Y|X).

# Parameters

  * `m`: The model with which to generate a prediction.
  * `X`: The input to be passed to `m`. Expected to be a matrix with dimensions dxn where n is the number of observations.

# Returns

The mode of each distribution returned by `m(X)`.
