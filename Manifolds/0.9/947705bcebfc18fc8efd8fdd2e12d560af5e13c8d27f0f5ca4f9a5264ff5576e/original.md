```
log(M::GeneralizedGrassmann, p, q)
```

Compute the logarithmic map on the [`GeneralizedGrassmann`](@ref) `M` $= \mathcal M=\mathrm{Gr}(n,k,B)$, i.e. the tangent vector `X` whose corresponding [`geodesic`](@extref `ManifoldsBase.geodesic-Tuple{AbstractManifold, Any, Any}`) starting from `p` reaches `q` after time 1 on `M`. The formula reads

$$
\log_p q = V⋅ \operatorname{atan}(S) ⋅ U^\mathrm{H},
$$

where $⋅^{\mathrm{H}}$ denotes the complex conjugate transposed or Hermitian. The matrices $U$ and $V$ are the unitary matrices, and $S$ is the diagonal matrix containing the singular values of the SVD-decomposition

$$
USV = (q^\mathrm{H}Bp)^{-1} ( q^\mathrm{H} - q^\mathrm{H}Bpp^\mathrm{H}).
$$

In this formula the $\operatorname{atan}$ is meant elementwise.
