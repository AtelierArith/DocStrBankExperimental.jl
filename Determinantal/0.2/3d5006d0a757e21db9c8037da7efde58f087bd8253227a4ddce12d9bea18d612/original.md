```
rff(X,m,σ)
```

Compute Random Fourier Features [rahimi2007random](@cite) for the Gaussian kernel matrix with input points X and parameter σ. Returns a random matrix M such that, in expectation $\mathbf{MM}^t = \mathbf{K}$, the Gaussian kernel matrix. M has 2*m columns. The higher m, the better the approximation.

## Examples

```@example
x = randn(2, 10) #10 points in dim 2
rff(ColVecs(x), 4, 1.0)
```

See also: gaussker, kernelmatrix
