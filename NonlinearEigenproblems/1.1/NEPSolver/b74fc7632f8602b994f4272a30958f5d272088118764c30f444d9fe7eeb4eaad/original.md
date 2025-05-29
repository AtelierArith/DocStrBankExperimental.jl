```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.DEP,::Type{ComputeY0ChebPEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

Computes the vector y0 used in [`iar_chebyshev`](@ref) given by

$$
 y_0 = \sum_{i=1}^N T_{i-1}(γ) x_i - \sum_{j=1}^m A_j \left( \sum_{i=1}^{N+1} T_{i-1}(-ρ \tau_j+γ) y_i \right )
$$

where T(c) is the vector containing $T_i(c)$ as coefficients, where $T_i$ is the i-th Chebyshev polynomial of the first kind.
