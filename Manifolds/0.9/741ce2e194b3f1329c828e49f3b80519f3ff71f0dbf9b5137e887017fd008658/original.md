```
exp(M::Grassmann, p, X)
```

Compute the exponential map on the [`Grassmann`](@ref) `M` $= \mathrm{Gr}(n,k)$ starting in `p` with tangent vector (direction) `X`. Let $X = USV$ denote the SVD decomposition of $X$. Then the exponential map is written using

$$
z = p V\cos(S)V^\mathrm{H} + U\sin(S)V^\mathrm{H},
$$

where $⋅^{\mathrm{H}}$ denotes the complex conjugate transposed or Hermitian and the cosine and sine are applied element wise to the diagonal entries of $S$. A final QR decomposition $z=QR$ is performed for numerical stability reasons, yielding the result as

$$
\exp_p X = Q.
$$
