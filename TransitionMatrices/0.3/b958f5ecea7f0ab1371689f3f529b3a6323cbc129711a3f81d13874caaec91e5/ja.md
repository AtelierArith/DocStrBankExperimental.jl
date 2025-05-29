```
extinction_cross_section(axi::AxisymmetricTransitionMatrix{CT, N}, λ=2π) where {CT, N}
```

粒子あたりの消失断面積を、Mishchenko et al. (2002) の式 (5.107) に従って、均一な方向分布で平均化して計算します。

$$
\left\langle C_{\text {ext }}\right\rangle=-\frac{2 \pi}{k_1^2} \operatorname{Re} \sum_{n=1}^{\infty} \sum_{m=0}^n\left(2-\delta_{m 0}\right)\left[T_{m n m n}^{11}(P)+T_{m n m n}^{22}(P)\right]
$$

パラメータ:

  * `𝐓`: 散乱体のT行列。
  * `λ`: ホスト媒質における入射波の波長。デフォルトは2πです。
