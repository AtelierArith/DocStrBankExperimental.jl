```
NoncentralChisq(ν, λ)
```

*非中心カイ二乗分布*は、`ν` 自由度と非中心性パラメータ `λ` を持ち、確率密度関数は次のようになります。

$$
f(x; \nu, \lambda) = \frac{1}{2} e^{-(x + \lambda)/2} \left( \frac{x}{\lambda} \right)^{\nu/4-1/2} I_{\nu/2-1}(\sqrt{\lambda x}), \quad x > 0
$$

これは、個々の平均 $\mu_i$ を持つ `ν` 個の独立な [`Normal`](@ref) 変数の二乗和の分布です。

$$
\lambda = \sum_{i=1}^\nu \mu_i^2
$$

```julia
NoncentralChisq(ν, λ)     # ν 自由度と非中心性パラメータ λ を持つ非中心カイ二乗分布

params(d)    # パラメータを取得します。すなわち (ν, λ)
```

外部リンク

  * [非中心カイ二乗分布 - Wikipedia](https://en.wikipedia.org/wiki/Noncentral_chi-squared_distribution)
