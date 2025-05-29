```
distance_profile(dist, Q, T; kwargs...)
```

Calculate the distance profile corresponding to sliding `Q` over `T` and measuring distances between time windows using `dist`

The output is a vector of length `length(T) - length(Q) + 1`. If inputs are matrices or higher-dimensional arrays, time is considered to be the last axis, and windows on the form `T[:, t:t+lastlength(Q)-1]`, where `lastlength` measures the length along the last axis, are compared.

Keyword arguments are sent to `dist`, which is called like this `dist(Q,T; kwargs...)`. `dist` can be a function or a distance from Distances.jl.

`distance_profile!(D, dist, Q, T; kwargs...)` is an in-place version.
