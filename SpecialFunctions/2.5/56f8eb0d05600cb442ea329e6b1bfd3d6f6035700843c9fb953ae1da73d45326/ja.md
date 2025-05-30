```
gamma_inc_temme(a, x, z)
```

Temmeの展開を用いて$P(a,x)$を計算します：

$$
1/2 * \operatorname{erfc}(\sqrt{y}) - e^{-y}/\sqrt{2\pi a} ⋅ T(a,\lambda)
$$

ここで

$$
T(a,\lambda) = \sum_{0}^{N} c_{k}(z)a^{-k}
$$

これは主に`a ≈ x`の領域で問題を解決し、大きな値のときに、最小最大近似の低精度バージョンです。

外部リンク: [DLMF 8.12.8](https://dlmf.nist.gov/8.12.8)

参照: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc) ```
