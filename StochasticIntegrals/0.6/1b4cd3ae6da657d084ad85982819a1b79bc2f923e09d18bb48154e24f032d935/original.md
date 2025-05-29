```
make_covariance_matrix(ito_set_::ItoSet, from::Real, to::Real)
```

Make a covariance matrix given an ItoSet and a period of time. This returns a Hermitian covariance matrix as well as a vector of symbols representing the axis labelling on this `Hermitian`.

### Inputs

  * `ito_set_` - An `ItoSet` you want to make a covariance matrix from.
  * `from` - The (numeric) time from which the covariance span starts.
  * `to` - The (numeric) time at which the covariance span ends.

### Returns

  * A `Hermitian` covariance matrix.
  * A `Vector{Symbol}` of labels for the covariance matrix.
