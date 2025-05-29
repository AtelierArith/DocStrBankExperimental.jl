```
pcasvd(Z, mean, tw; ...)
```

Compute and return a PCA model based on singular value decomposition of a centralized sample matrix `Z`.

**Parameters:**

  * `Z`: a matrix of centralized samples.
  * `mean`: The mean vector of the **original** samples, which can be a vector of length `d`,         or an empty vector `Float64[]` indicating a zero mean.
  * `n`: a number of samples.

*Note:* This function accepts two keyword arguments: `maxoutdim` and `pratio`.
