```
scattering_cross_section(𝐓::AbstractTransitionMatrix{CT, N}, λ=2π) where {CT, N}
```

粒子あたりの散乱断面積を、Mishchenko et al. (2002) の式 (5.140) に従って、均一な方向分布で平均化して計算します。

$$
\left\langle C_{\mathrm{sca}}\right\rangle=\frac{2 \pi}{k_1^2} \sum_{n=1}^{\infty} \sum_{m=-n}^n \sum_{n^{\prime}=1}^{\infty} \sum_{m^{\prime}=-n^{\prime}}^{n^{\prime}} \sum_{k=1}^2 \sum_{l=1}^2\left|T_{m n m^{\prime} n^{\prime}}^{k l}(P)\right|^2
$$

パラメータ:

  * `𝐓`: 散乱体のT行列。
  * `λ`: ホスト媒質における入射波の波長。デフォルトは2πです。
