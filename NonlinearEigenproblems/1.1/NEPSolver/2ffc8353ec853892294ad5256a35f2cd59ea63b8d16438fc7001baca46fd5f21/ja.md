```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.PEP,::Type{ComputeY0ChebPEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

[`iar_chebyshev`](@ref) で与えられるベクトル y0 を計算します。

$$
 y_0 = \sum_{j=0}^{d-1} A_{j+1} x D^j T(c) - y T(c)
$$

ここで、T(c) は $T_i(c)$ を係数として含むベクトルであり、$T_i$ は第 i の一種のチェビシェフ多項式で、$D$ はチェビシェフ基底における導関数行列です。
