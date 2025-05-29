```
exp(M::GeneralizedGrassmann, p, X)
```

Compute the exponential map on the [`GeneralizedGrassmann`](@ref) `M` $= \mathrm{Gr}(n,k,B)$ starting in `p` with tangent vector (direction) `X`. Let $X^{\mathrm{H}}BX = USV$ denote the SVD decomposition of $X^{\mathrm{H}}BX$. Then the exponential map is written using

$$
\exp_p X = p V\cos(S)V^\mathrm{H} + U\sin(S)V^\mathrm{H},
$$

where $⋅^{\mathrm{H}}$ denotes the complex conjugate transposed or Hermitian and the cosine and sine are applied element wise to the diagonal entries of $S$.
