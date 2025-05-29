```
SimpleCovariance
```

Creates an `SimpleCovariance` struct. This is a simplified version of `ForwardCovariance` and is designed for `ItoIntegral`s that are constant (so correlations do not need to be recalculated). This computational saving is the only advantage - `ForwardCovariance` is more general. It contains the same elements as a `ForwardCovariance`:

  * An Itoset
  * The time from which the covariance period starts.
  * The time to which the covariance period extends to.

And in the constructor the following items are generated and stored in the object:

  * A covariance matrix
  * Labels for the covariance matrix.
  * The cholesky decomposition of the covariance matrix.
  * The inverse of the covariance matrix.
  * The determinant of the covariance matrix.

The constructors are:

```
SimpleCovariance(ito_set_::ItoSet, from_::Real, to_::Real;
     calculate_chol::Bool = true, calculate_inverse::Bool = true, calculate_determinant::Bool = true)
```
