```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.PEP,::Type{ComputeY0ChebPEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

Computes the vector y0 used in [`iar_chebyshev`](@ref) given by

$$
 y_0 = \sum_{j=0}^{d-1} A_{j+1} x D^j T(c) - y T(c)
$$

where T(c) is the vector containing $T_i(c)$ as coefficients, where $T_i$ is the i-th Chebyshev polynomial of the first kind and $D$ is the derivation matrix in Chebyshev basis.
