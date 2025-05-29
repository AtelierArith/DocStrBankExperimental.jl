```
pcacov(C, mean; ...)
```

Compute and return a PCA model based on eigenvalue decomposition of a given covariance matrix `C`.

**Parameters:**

  * `C`: The covariance matrix of the samples.
  * `mean`: The mean vector of original samples, which can be a vector of length `d`,          or an empty vector `Float64[]` indicating a zero mean.

*Note:* This function accepts two keyword arguments: `maxoutdim` and `pratio`.
