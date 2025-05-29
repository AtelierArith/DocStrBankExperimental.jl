```
gaussker(X,σ)
```

Compute the Gaussian kernel matrix for points X and parameter σ, ie. a matrix with entry i,j equal to $\exp(-\frac{(x_i-x_j)^2}{2σ^2})$

If σ is missing, it is set using the median heuristic. If the number of points is very large, the median is estimated on a random subset.

```@example
x = randn(2, 6)
gaussker(ColVecs(x), 0.1)
```

See also: rff, KernelMatrix:kernelmatrix
