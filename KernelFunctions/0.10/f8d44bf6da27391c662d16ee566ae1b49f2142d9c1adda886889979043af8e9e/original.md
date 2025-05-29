```
LinearMixingModelKernel(k::Kernel, H::AbstractMatrix)
LinearMixingModelKernel(Tk::AbstractVector{<:Kernel},Th::AbstractMatrix)
```

Kernel associated with the linear mixing model, taking a vector of `Q` kernels and a `Q × m` mixing matrix H for a function with `m` outputs. Also accepts a single kernel `k` for use across all `Q` basis vectors. 

# Definition

For inputs $x, x'$ and output dimensions $p, p'$, the kernel is defined as[^BPTHST]

$$
k\big((x, p), (x, p')\big) = H_{:,p}K(x, x')H_{:,p'}
$$

where $K(x, x') = Diag(k_1(x, x'), ..., k_Q(x, x'))$ with zero off-diagonal entries. $H_{:,p}$ is the $p$-th column (`p`-th output) of $H \in \mathbb{R}^{Q \times m}$ representing $Q$ basis vectors for the $m$ dimensional output space of $f$. $k_1, \ldots, k_Q$ are $Q$ kernels, one for each latent process, $H$ is a mixing matrix of $Q$ basis vectors spanning the output space.

[^BPTHST]: Wessel P. Bruinsma, Eric Perim, Will Tebbutt, J. Scott Hosking, Arno Solin, Richard E. Turner (2020). [Scalable Exact Inference in Multi-Output Gaussian Processes](https://arxiv.org/pdf/1911.06287.pdf).
