```
SinkhornEpsilonScaling(algorithm::Sinkhorn; factor=1//2, steps=5)
```

Construct an ε-scaling Sinkhorn algorithm for solving an entropically regularized optimal transport problem.

The function uses the specified Sinkhorn `algorithm` with `steps` ε-scaling steps with scaling factor `factor`. It sequentially solves the entropically regularized optimal transport with regularization parameters

$$
\varepsilon_i := \varepsilon \lambda^{i-k}, \qquad (i = 1,\ldots,k),
$$

where $\lambda$ is the scaling factor and $k$ the number of scaling steps.
