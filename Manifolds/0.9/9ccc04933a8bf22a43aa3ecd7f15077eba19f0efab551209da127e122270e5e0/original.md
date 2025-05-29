```
log(G::GeneralLinear, p, q)
```

Compute the logarithmic map on the [`GeneralLinear(n)`](@ref) group.

The algorithm proceeds in two stages. First, the point $r = p^{-1} q$ is projected to the nearest element (under the Frobenius norm) of the direct product subgroup $\mathrm{O}(n) × S^+$, whose logarithmic map is exactly computed using the matrix logarithm. This initial tangent vector is then refined using the [`NLSolveInverseRetraction`](@extref `ManifoldsBase.NLSolveInverseRetraction`).

For `GeneralLinear(n, ℂ)`, the logarithmic map is instead computed on the realified supergroup `GeneralLinear(2n)` and the resulting tangent vector is then complexified.

Note that this implementation is experimental.
