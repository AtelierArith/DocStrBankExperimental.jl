```
GaussianProcess(func, mean=0)
```

Gaussian process with given geostatistical `func`tion (e.g. variogram) and `mean`.

## Examples

```julia
# univariate processes
GaussianProcess(GaussianVariogram())
GaussianProcess(SphericalCovariance(), 0.5)

# multivariate processes
GaussianProcess(LinearTransiogram(), [0.5, 0.5])
```
