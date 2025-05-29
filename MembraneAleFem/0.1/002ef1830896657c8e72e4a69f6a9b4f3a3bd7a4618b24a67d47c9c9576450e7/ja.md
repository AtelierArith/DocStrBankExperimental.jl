```
GaussPointsξ(ngp::Int64)
```

重み $\hat{w}_k$ と点 $ξ_k$ は、1次元の積分を近似するための区間 $[-1, +1]$ 上にあります。

この構造体には3つのフィールドがあります：

  * `ngp` –> ガウス求積点の数
  * `ξs`  –> 点のセット $ξ_k$
  * `ws`  –> 重みのセット $\hat{w}_k$

[Wikipedia: ガウス求積](https://en.wikipedia.org/wiki/Gaussian_quadrature#Gauss.E2.80.93Legendre_quadrature) からの計算。
