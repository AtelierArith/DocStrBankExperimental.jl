```
IntrinsicCoregionMOKernel(; kernel::Kernel, B::AbstractMatrix)
```

Kernel associated with the intrinsic coregionalization model.

# Definition

For inputs $x, x'$ and output dimensions $p, p'$, the kernel is defined as[^ARL]

$$
k\big((x, p), (x', p'); B, \tilde{k}\big) = B_{p, p'} \tilde{k}\big(x, x'\big),
$$

where $B$ is a positive semidefinite matrix of size $m \times m$, with $m$ being the number of outputs, and $\tilde{k}$ is a scalar-valued kernel shared by the latent processes.

[^ARL]: M. Álvarez, L. Rosasco, & N. Lawrence (2012). [Kernels for Vector-Valued Functions: a Review](https://arxiv.org/pdf/1106.6251.pdf).
