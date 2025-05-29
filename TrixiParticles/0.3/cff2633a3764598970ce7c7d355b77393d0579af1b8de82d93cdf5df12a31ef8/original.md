```
WendlandC4Kernel{NDIMS}()
```

Wendland C4 kernel [Wendland1995](@cite), a piecewise polynomial function designed to have compact support and to be four times continuously differentiable everywhere. Given by

$$
 W(r, h) = \frac{1}{h^d} w(r/h)
$$

with

$$
w(q) = \sigma \begin{cases}
    (1 - q/2)^6 (35q^2 / 12 + 3q + 1)   & \text{if } 0 \leq q < 2, \\
    0                                   & \text{if } q \geq 2,
\end{cases}
$$

where $d$ is the number of dimensions and $\sigma$ is a normalization factor dependent on the dimension. The normalization factor $\sigma$ is $9 / \pi$ in two dimensions or $495 / 32\pi$ in three dimensions.

This kernel function has a compact support of $[0, 2h]$.

For a detailed discussion on Wendland functions and their applications in SPH, see [Dehnen (2012)](@cite Dehnen2012). The smoothness of these functions is also the largest disadvantage as they lose details at sharp corners.

The smoothing length is typically in the range $[1.5\delta, 2.3\delta]$, where $\delta$ is the typical particle spacing.

For general information and usage see [Smoothing Kernels](@ref smoothing_kernel).
