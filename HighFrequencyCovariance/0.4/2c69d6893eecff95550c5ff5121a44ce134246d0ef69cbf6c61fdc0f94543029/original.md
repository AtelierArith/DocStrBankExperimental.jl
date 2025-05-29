```
StochasticIntegrals.ItoSet(covariance_matrix::CovarianceMatrix{<:Real})
```

Convert a `CovarianceMatrix` into an `ItoSet` from the StochasticIntegrals package. This package can then be used to do things like generate draws from the Multivariate Gaussian corresponding to the covariance matrix and other things.

### Inputs

  * `covariance_matrix` - The `CovarianceMatrix` that you want to convert into an `StochasticIntegrals.ItoSet`

### Returns

  * A `StochasticIntegrals.ItoSet` struct.

### Example

```
using Dates
covar = CovarianceMatrix(make_random_psd_matrix_from_wishart(5), rand(5), [:A,:B,:C,:D,:E], Dates.Hour(1))
iset = ItoSet(covar)
# To see how this is used for something useful you can look at the get_draws function.
```
