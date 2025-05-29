```
ForwardCovariance
```

Creates an `ForwardCovariance` struct. This contains :

  * An `Itoset`.
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
ForwardCovariance(ito_set_::ItoSet, from_::Real, to_::Real;
                  calculate_chol::Bool = true, calculate_inverse::Bool = true, calculate_determinant::Bool = true)
ForwardCovariance(ito_set_::ItoSet, from::Union{Date,DateTime}, to::Union{Date,DateTime})
ForwardCovariance(old_ForwardCovariance::ForwardCovariance, from::Real, to::Real)
ForwardCovariance(old_ForwardCovariance::ForwardCovariance, from::Union{Date,DateTime}, to::Union{Date,DateTime})
```
