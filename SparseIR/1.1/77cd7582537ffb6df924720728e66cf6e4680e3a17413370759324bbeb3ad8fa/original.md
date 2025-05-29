```
MatsubaraSampling(basis; positive_only=false,
                  sampling_points=default_matsubara_sampling_points(basis; positive_only),
                  factorize=true)
```

Construct a `MatsubaraSampling` object. If not given, the `sampling_points` are chosen as the (discrete) extrema of the highest-order basis function in Matsubara. This turns out to be close to optimal with respect to conditioning for this size (within a few percent).

By setting `positive_only=true`, one assumes that functions to be fitted are symmetric in Matsubara frequency, i.e.:

$$
    Ĝ(iν) = conj(Ĝ(-iν))
$$

or equivalently, that they are purely real in imaginary time. In this case, sparse sampling is performed over non-negative frequencies only, cutting away half of the necessary sampling space. `factorize` controls whether the SVD decomposition is computed.
