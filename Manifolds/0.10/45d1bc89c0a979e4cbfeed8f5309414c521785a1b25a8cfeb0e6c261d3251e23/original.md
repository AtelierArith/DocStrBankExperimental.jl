```
inner(M::Grassmann, p, X, Y)
```

Compute the inner product for two tangent vectors `X`, `Y` from the tangent space of `p` on the [`Grassmann`](@ref) manifold `M`. The formula reads

$$
g_p(X,Y) = \operatorname{tr}(X^{\mathrm{H}}Y),
$$

where $⋅^{\mathrm{H}}$ denotes the complex conjugate transposed or Hermitian.
