```
projection(M::KernelPCA)
```

Return the projection matrix (of size $n \times p$). Each column of the projection matrix corresponds to an eigenvector, and $n$ is a number of observations.

The principal components are arranged in descending order of the corresponding eigenvalues.
