```
statespace_sampler(region [, seed = 42]) → sampler, isinside
```

A function that facilitates sampling points randomly and uniformly in a state space `region`. It generates two functions:

  * `sampler` is a 0-argument function that when called generates a random point inside a state space `region`. The point is always a `Vector` for type stability irrespectively of dimension. Generally, the generated point should be *copied* if it needs to be stored. (i.e., calling `sampler()` utilizes a shared vector) `sampler` is a thread-safe function.
  * `isinside` is a 1-argument function that returns `true` if the given state space point is inside the `region`.

The `region` can be an instance of any of the following types (input arguments if not specified are vectors of length `D`, with `D` the state space dimension):

  * `HSphere(radius::Real, center)`: points *inside* the hypersphere (boundary excluded). Convenience method `HSphere(radius::Real, D::Int)` makes the center a `D`-long vector of zeros.
  * `HSphereSurface(radius, center)`: points on the hypersphere surface. Same convenience method as above is possible.
  * `HRectangle(mins, maxs)`: points in [min, max) for the bounds along each dimension.

The random number generator is always `Xoshiro` with the given `seed`.
