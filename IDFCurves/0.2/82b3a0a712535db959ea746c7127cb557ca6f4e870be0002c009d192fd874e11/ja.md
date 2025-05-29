```
SimpleScaling(d₀::Real, μ₀::Real, σ₀::Real, ξ::Real, α::Real)
```

シンプルスケーリング分布タイプを構築します。

## 詳細

**TODO**

$$
\mu_d = \mu_0 \left(\frac{d}{d_0} \right) ^{-\alpha} \qquad    \sigma_d = \sigma_0 \left(\frac{d}{d_0} \right) ^{-\alpha} \qquad    \xi_d = \xi
$$

## 参考文献

Koutsoyiannis, D., Kozonis, D. and Manetas, A. (1998).  降雨強度-持続時間-頻度関係を研究するための数学的枠組み, *Journal of Hydrology*, 206(1-2), 118-135, https://doi.org/10.1016/S0022-1694(98)00097-3. ```
