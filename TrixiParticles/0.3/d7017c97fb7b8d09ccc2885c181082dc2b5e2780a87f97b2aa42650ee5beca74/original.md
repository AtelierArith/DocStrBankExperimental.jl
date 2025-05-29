```
Poly6Kernel{NDIMS}()
```

Poly6 kernel, a commonly used kernel in SPH literature [Mueller2003](@cite), especially in computer graphics contexts. It is defined as

$$
W(r, h) = \frac{1}{h^d} w(r/h)
$$

with

$$
w(q) = \sigma \begin{cases}
    (1 - q^2)^3    & \text{if } 0 \leq q < 1, \\
    0              & \text{if } q \geq 1,
\end{cases}
$$

where $d$ is the number of dimensions and $\sigma$ is a normalization factor that depends on the dimension. The normalization factor $\sigma$ is $4 / \pi$ in two dimensions or $315 / 64\pi$ in three dimensions.

This kernel function has a compact support of $[0, h]$.

Poly6 is well-known for its computational simplicity, though it's worth noting that there are other kernels that might offer better accuracy for hydrodynamic simulations. Furthermore, its derivatives are not that smooth, which can lead to stability problems. It is also susceptible to clumping.

The smoothing length is typically in the range $[1.5\delta, 2.5\delta]$, where $\delta$ is the typical particle spacing.

For general information and usage see [Smoothing Kernels](@ref smoothing_kernel).
