```
SchoenbergQuinticSplineKernel{NDIMS}()
```

Quintic spline kernel by [Schoenberg (1946)](@cite Schoenberg1946), given by

$$
    W(r, h) = \frac{1}{h^d} w(r/h)
$$

with

$$
w(q) = \sigma \begin{cases}
    (3 - q)^5 - 6(2 - q)^5 + 15(1 - q)^5    & \text{if } 0 \leq q < 1, \\
    (3 - q)^5 - 6(2 - q)^5                  & \text{if } 1 \leq q < 2, \\
    (3 - q)^5                               & \text{if } 2 \leq q < 3, \\
    0                                       & \text{if } q \geq 3,
\end{cases}
$$

where $d$ is the number of dimensions and $\sigma$ is a normalization constant given by $\sigma =[\frac{1}{120}, \frac{7}{478 \pi}, \frac{1}{120\pi}]$ in $[1, 2, 3]$ dimensions.

This kernel function has a compact support of $[0, 3h]$.

For an overview of Schoenberg cubic, quartic and quintic spline kernels including normalization factors, see [Price (2012)](@cite Price2012). For an analytic formula for higher order Schoenberg kernels, see [Monaghan (1985)](@cite Monaghan1985).

The largest disadvantage of Schoenberg Spline Kernel are the rather non-smooth first derivative, which can lead to increased noise compared to other kernel variants.

The smoothing length is typically in the range $[1.1\delta, 1.5\delta]$, where $\delta$ is the typical particle spacing.

For general information and usage see [Smoothing Kernels](@ref smoothing_kernel).
