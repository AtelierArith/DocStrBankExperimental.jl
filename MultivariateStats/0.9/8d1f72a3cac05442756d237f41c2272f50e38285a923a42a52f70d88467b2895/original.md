```
fit(LinearDiscriminant, Xp, Xn; covestimator = SimpleCovariance())
```

Performs LDA given both positive and negative samples. The function accepts follwing parameters:

**Parameters**

  * `Xp`: The sample matrix of the positive class.
  * `Xn`: The sample matrix of the negative class.

**Keyword arguments:**

  * `covestimator`: Custom covariance estimator for between-class covariance. The covariance matrix will be calculated as `cov(covestimator_between, #=data=#; dims=2, mean=zeros(#=...=#)`. Custom covariance estimators, available in other packages, may result in more robust discriminants for data with more features than observations.
