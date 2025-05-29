```
WendlandC6Kernel{NDIMS}()
```

Wendland C6 kernel [Wendland1995](@cite), a piecewise polynomial function designed to have compact support and to be six times continuously differentiable everywhere. Given by:

$$
W(r, h) = \frac{1}{h^d} w(r/h)
$$

with:

$$
w(q) = \sigma \begin{cases}
    (1 - q / 2)^8 (4q^3 + 25q^2 / 4 + 4q + 1)   & \text{if } 0 \leq q < 2, \\
    0                                           & \text{if } q \geq 2,
\end{cases}
$$

where $d$ is the number of dimensions and $\sigma$ is a normalization factor dependent on the dimension. The normalization factor $\sigma$ is $78 / 7 \pi$ in two dimensions or $1365 / 64\pi$ in three dimensions.

This kernel function has a compact support of $[0, 2h]$.

For a detailed discussion on Wendland functions and their applications in SPH, [Dehnen (2012)](@cite Dehnen2012). The smoothness of these functions is also the largest disadvantage as they lose details at sharp corners.

The smoothing length is typically in the range $[1.7\delta, 2.5\delta]$, where $\delta$ is the typical particle spacing.

For general information and usage see [Smoothing Kernels](@ref smoothing_kernel).
