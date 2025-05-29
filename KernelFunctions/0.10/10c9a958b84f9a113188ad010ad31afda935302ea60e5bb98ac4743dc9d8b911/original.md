```
ScaledKernel(k::Kernel, σ²::Real=1.0)
```

Scaled kernel derived from `k` by multiplication with variance `σ²`.

# Definition

For inputs $x, x'$, the scaled kernel $\widetilde{k}$ derived from kernel $k$ by multiplication with variance $\sigma^2 > 0$ is defined as

$$
\widetilde{k}(x, x'; k, \sigma^2) = \sigma^2 k(x, x').
$$
