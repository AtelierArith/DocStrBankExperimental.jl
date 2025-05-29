```
LogLikeMLE(DM::DataModel) -> Real
```

Returns the value of the log-likelihood $\ell$ when evaluated at the maximum likelihood estimate, i.e. $\ell(\mathrm{data} \, | \, \theta_\text{MLE})$. For performance reasons, this value is stored as a part of the `DataModel` type.
