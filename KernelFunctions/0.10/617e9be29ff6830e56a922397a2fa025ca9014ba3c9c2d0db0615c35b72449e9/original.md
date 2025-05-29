```
LatentFactorMOKernel(g::AbstractVector{<:Kernel}, e::MOKernel, A::AbstractMatrix)
```

Kernel associated with the semiparametric latent factor model.

# Definition

For inputs $x, x'$ and output dimensions $p_x, p_{x'}'$, the kernel is defined as[^STJ]

$$
k\big((x, p_x), (x, p_{x'})\big) = \sum^{Q}_{q=1} A_{p_xq}g_q(x, x')A_{p_{x'}q}
                                   + e\big((x, p_x), (x', p_{x'})\big),
$$

where $g_1, \ldots, g_Q$ are $Q$ kernels, one for each latent process, $e$ is a multi-output kernel for $m$ outputs, and $A$ is a matrix of weights for the kernels of size $m \times Q$.

[^STJ]: M. Seeger, Y. Teh, & M. I. Jordan (2005). [Semiparametric Latent Factor Models](https://infoscience.epfl.ch/record/161465/files/slfm-long.pdf).
