```
TauSampling(basis; sampling_points=default_tau_sampling_points(basis), factorize=true)
```

Construct a `TauSampling` object. If not given, the `sampling_points` are chosen as the extrema of the highest-order basis function in imaginary time. This turns out to be close to optimal with respect to conditioning for this size (within a few percent). `factorize` controls whether the SVD decomposition is computed.
