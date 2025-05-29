```
update!(sc::SimpleCovariance, from::Real, to::Real)
```

This takes a `SimpleCovariance` and updates it for a new  span in time. The new span in time is between from and to. For `SimpleCovariance` this is done by just adjusting the covariances for the new time span (with corresponding adjustments) to the cholesky, inverse, etc.

The corresponding technique for a `ForwardCovariance` (which is also a `StochasticIntegralsCovariance`) is to feed it into a new `ForwardCovariance` constructor which will recalculate for the new span.

### Inputs

  * `sc` - The `SimpleCovariance` struct.
  * `from` - The time from which you want the covariance for.
  * `to` - The time to which you want the covariance for.

### Returns

Nothing. It juts updates the sc struct you pass in as an input.
