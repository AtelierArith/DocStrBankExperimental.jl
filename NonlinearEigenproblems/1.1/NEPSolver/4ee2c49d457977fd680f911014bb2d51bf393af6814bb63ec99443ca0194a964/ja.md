```
y0 = compute_y0_cheb([eltype],nep::NEPTypes.NEP,::Type{ComputeY0ChebNEP},X,Y,M0inv,precomp::AbstractPrecomputeData)
```

[`iar_chebyshev`](@ref) で定義されるベクトル y0 を計算します。

$$
 y_0 =\left( \sum_{i=0}^{N-1} B \left( \frac{d}{d \theta} \right) \hat T_i(\theta) x_i \right)(0) - \sum_{i=0}^{N} T_i(c) y_i
$$

ここで、$T_i$ は第 i の一様チェビシェフ多項式、$ \ hat T_i$ は区間 [a,b] の第 i の一様チェビシェフ多項式です。一般的な `nep` に対して、この量は多項式をモノミアル基底に変換することによって計算されます。この手順は、多くの反復が必要な場合、数値的に不安定になる可能性があります。特定の `nep` に対して閉じた式が利用可能な場合は、この関数をオーバーロードすることをお勧めします。
