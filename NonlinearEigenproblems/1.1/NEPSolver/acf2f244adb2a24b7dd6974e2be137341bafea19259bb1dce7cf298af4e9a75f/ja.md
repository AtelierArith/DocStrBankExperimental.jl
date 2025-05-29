```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.SPMF_NEP,::Type{ComputeY0ChebPEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

[`iar_chebyshev`](@ref) で与えられるベクトル y0 を計算します。

$$
 y_0= \sum_{j=0}^{m} M^{(j)}(\mu) X b_j \left( D_N \right) T_N(c) - Y T_N(c)
$$

ここで、T(c) は $T_i(c)$ を係数として含むベクトルであり、$T_i$ は第一種のチェビシェフ多項式の i 番目のもので、$b_j(\lambda)=(f_j(0)-f_j(\lambda))/\lambda=f[\lambda,0]$ は商の差分です。
