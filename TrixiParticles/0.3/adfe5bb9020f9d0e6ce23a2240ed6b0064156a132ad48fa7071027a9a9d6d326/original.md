```
SpikyKernel{NDIMS}()
```

The Spiky kernel is another frequently used kernel in SPH, especially due to its desirable properties in preserving features near boundaries in fluid simulations [Mueller2003](@cite). It is defined as:

$$
 W(r, h) = \frac{1}{h^d} w(r/h)
$$

with:

$$
w(q) = \sigma \begin{cases}
    (1 - q)^3    & \text{if } 0 \leq q < 1, \\
    0            & \text{if } q \geq 1,
\end{cases}
$$

where $d$ is the number of dimensions and the normalization factor $\sigma$ is $10 / \pi$ in two dimensions or $15 / \pi$ in three dimensions.

This kernel function has a compact support of $[0, h]$.

The Spiky kernel is particularly known for its sharp gradients, which can help to preserve sharp features in fluid simulations, especially near solid boundaries. These sharp gradients at the boundary are also the largest disadvantage as they can lead to instability.

The smoothing length is typically in the range $[1.5\delta, 3.0\delta]$, where $\delta$ is the typical particle spacing.

For general information and usage see [Smoothing Kernels](@ref smoothing_kernel).
