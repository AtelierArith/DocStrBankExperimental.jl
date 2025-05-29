```
LpDistance <: ProbabilityDensityDM
```

$$
\ell^p
$$

距離識別測度は、確率密度および時間周波数に基づくエネルギーマップのためのものです。デフォルトの $p$ 値は 2 に設定されています。

方程式:

$$
W(q,r) = ||q-r||_p^p = \sum_{i=1}^n (q_i - r_i)^p
$$
