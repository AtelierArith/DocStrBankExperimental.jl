```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.NEP,::Type{ComputeY0ChebNEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

Computes the vector y0 used in [`iar_chebyshev`](@ref) defined as

$$
 y_0 =\left( \sum_{i=0}^{N-1} B \left( \frac{d}{d \theta} \right) \hat T_i(\theta) x_i \right)(0) - \sum_{i=0}^{N} T_i(c) y_i
$$

where $T_i$ is the i-th Chebyshev polynomial of the first kind, $ \ hat T_i$ is the i-th Chebyshev polynomial of the first kind for the interval [a,b]. For a generic `nep`, this quantity is computed by converting polynomials in monomial basis. This procedure may be numerical unstable if many iterations are required. If for the specific `nep` a closed formula is available, we suggest to overload this function.
