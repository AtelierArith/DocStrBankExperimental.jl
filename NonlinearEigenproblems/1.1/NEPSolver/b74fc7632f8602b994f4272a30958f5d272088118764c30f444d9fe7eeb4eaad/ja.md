```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.DEP,::Type{ComputeY0ChebPEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

[`iar_chebyshev`](@ref) で与えられるベクトル y0 を計算します。

$$
 y_0 = \sum_{i=1}^N T_{i-1}(γ) x_i - \sum_{j=1}^m A_j \left( \sum_{i=1}^{N+1} T_{i-1}(-ρ \tau_j+γ) y_i \right )
$$

ここで、T(c) は $T_i(c)$ を係数として含むベクトルであり、$T_i$ は第一種の i 番目のチェビシェフ多項式です。
