```
NormalizedKernel(k::Kernel)
```

A normalized kernel derived from `k`.

# Definition

For inputs $x, x'$, the normalized kernel $\widetilde{k}$ derived from kernel $k$ is defined as

$$
\widetilde{k}(x, x'; k) = \frac{k(x, x')}{\sqrt{k(x, x) k(x', x')}}.
$$
