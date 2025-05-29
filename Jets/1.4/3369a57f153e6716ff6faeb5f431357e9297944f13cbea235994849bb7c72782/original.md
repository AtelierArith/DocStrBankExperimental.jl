```
JetSSpace(_T, n, M, map::F)
```

Construct and return a symmetric space `JetSSpace`.

# parameters

  * `_T` is the type, usually `Complex{Float32}` or `Complex{Float64}`.
  * `n` is a tuple that defines the dimensionality of the space.
  * `M` is a tuple that defines which dimensions are symmetric. Note that currently only a single symmetric dimension is supported by the API.
  * `F` is a function that maps indices for the symmetric dimension, described below.

An example requiring a `JetSSpace` is the Fourier transform: the Fourier transform of a real vector is in a complex space with Hermittian symmetry. Only the positive frequencies are needed, and the spectrum at negative frequencies is the Hermittian conjugate of the spectrum at the corresponding positive frequencies: `S(-f) = conj(S(f)`. For this example the map `F` is a function that returns the multi-dimensional index of `f` when given the multi-dimensional index of `-f`.

See also: `JopFft` in the `JetPackTransforms` package.
