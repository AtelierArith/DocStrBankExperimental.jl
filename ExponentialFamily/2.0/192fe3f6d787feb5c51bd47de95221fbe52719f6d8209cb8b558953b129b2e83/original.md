```
JointNormal{D, S}
```

`JointNormal` is an auxilary structure used for the joint marginal over Normally distributed variables. `JointNormal` stores a vector with the original dimensionalities (ds), so statistics can later be re-separated.

Use `ExponentialFamily.getcomponent(joint, index)` to get a specific component of the joint distribution.

# Fields

  * `dist`: joint distribution (typically just a big `MvNormal` distribution, but maybe a tuple of individual means and covariance matrices)
  * `ds`: a tuple with the original dimensionalities of individual `Normal` distributions
  * `ds[k] = (n,)` where `n` is an integer indicates `Multivariate` normal of size `n`
  * `ds[k] = ()` indicates `Univariate` normal
