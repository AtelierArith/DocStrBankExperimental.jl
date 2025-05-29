```julia
calcProductGaussians(
    M,
    kernels;
    μ0,
    weight,
    do_transport_correction
)

```

EXPERIMENTAL: On-manifold product of Gaussians.

DevNotes

  * FIXME do product of concentrated Gaussians on Lie group (approximation):

      * See Section 3.2 and 4 of [Ge, van Goor, Mahony: A Geometric Perspective on using Gaussian Distributions on Lie Groups, 2024].
      * Also see upstream utils, https://juliamanifolds.github.io/Manifolds.jl/stable/features/distributions.html
  * FIXME is parallel transport needed when multiplying with covariances from difffent tangent spaces?
