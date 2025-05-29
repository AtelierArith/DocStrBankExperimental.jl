```
scattering_cross_section(axi::AxisymmetricTransitionMatrix{CT, N}, λ=2π) where {CT, N}
```

粒子あたりの散乱断面積を、Mishchenko et al. (2002) の式 (5.141) に従って、均一な方向分布で平均化して計算します。

$$
\left\langle C_{\text {sca }}\right\rangle=\frac{2 \pi}{k_1^2} \sum_{n=1}^{\infty} \sum_{n^{\prime}=1}^{\infty} \sum_{m=0}^{\min \left(n, n^{\prime}\right)} \sum_{k=1}^2 \sum_{l=1}^2\left(2-\delta_{m 0}\right)\left|T_{m n m n^{\prime}}^{k l}(P)\right|^2
$$

パラメータ:

  * `𝐓`: 散乱体のT行列。
  * `λ`: ホスト媒質における入射波の波長。デフォルトは2πです。
