```
GaussianKernel{NDIMS}()
```

Gaussian kernel given by

$$
W(r, h) = \frac{\sigma_d}{h^d} e^{-r^2/h^2}
$$

where $d$ is the number of dimensions and

  * $\sigma_2 = \frac{1}{\pi}$ for 2D,
  * $\sigma_3 = \frac{1}{\pi^{3/2}}$ for 3D.

This kernel function has an infinite support, but in practice, it's often truncated at a certain multiple of $h$, such as $3h$.

In this implementation, the kernel is truncated at $3h$, so this kernel function has a compact support of $[0, 3h]$.

The smoothing length is typically in the range $[1.0\delta, 1.5\delta]$, where $\delta$ is the typical particle spacing.

For general information and usage see [Smoothing Kernels](@ref smoothing_kernel).

Note: This truncation makes this Kernel not conservative, which is beneficial in regards to stability but makes it less accurate.
