```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.SPMF_NEP,::Type{ComputeY0ChebPEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

Computes the vector y0 used in [`iar_chebyshev`](@ref) given by

$$
 y_0= \sum_{j=0}^{m} M^{(j)}(\mu) X b_j \left( D_N \right) T_N(c) - Y T_N(c)
$$

where T(c) is the vector containing $T_i(c)$ as coefficients, where $T_i$ is the i-th Chebyshev polynomial of the first kind and $b_j(\lambda)=(f_j(0)-f_j(\lambda))/\lambda=f[\lambda,0]$ are divided differences.
