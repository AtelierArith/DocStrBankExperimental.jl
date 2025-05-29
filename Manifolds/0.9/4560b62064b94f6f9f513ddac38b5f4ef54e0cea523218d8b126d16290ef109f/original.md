```
log(M::Rotations, p, q)
```

Compute the logarithmic map on the [`Rotations`](@ref) manifold `M` which is given by

$$
\log_p q = \operatorname{log}(p^{\mathrm{T}}q)
$$

where $\operatorname{Log}$ denotes the matrix logarithm. For numerical stability, the result is projected onto the set of skew symmetric matrices.

For antipodal rotations the function returns deterministically one of the tangent vectors that point at `q`.
