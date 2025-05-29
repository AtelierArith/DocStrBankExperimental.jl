DiscreteGaussianImpulseResponse <: DiscreteImpulseResponse

If there are fewer basis functions than lags, then the means are evenly spaced between the endpoints of `[1, L]` such that the distance to the nearest mean or endpoint is the same everywhere. As a result, you can only have a means located at the endpoints if the number of basis functions is at least as great as the number of lags.
