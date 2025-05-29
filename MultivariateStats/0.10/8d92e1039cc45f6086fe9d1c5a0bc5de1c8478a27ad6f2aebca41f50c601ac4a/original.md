```
reconstruct(M::KernelPCA, y)
```

Approximately reconstruct observations, given in `y`, to the original space using the kernel PCA model `M`.

Here, `y` can be either a vector of length `p` or a matrix where each column gives the principal components for an observation.
