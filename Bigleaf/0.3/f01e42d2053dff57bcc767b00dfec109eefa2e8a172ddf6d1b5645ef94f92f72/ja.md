```
roughness_length_heat(z0m, kB_h)
```

# 引数

  * `z0m` : 運動量の粗さ長さ (m)。[`roughness_parameters`](@ref) によって計算できます。
  * `kB_h` : 熱伝達の kB^(-1) パラメータ、[`aerodynamic_conductance!`](@ref) の出力

# 詳細

水と熱の粗さ長さ (z0h) は、関係式から計算されます (例: Verma 1989):

$$
{k_B}_h = ln(z_{0m}/z_{0h})
$$

したがって:

$$
z_{0h} = z_{0m} / e^{k_{B_h}}
$$

# 参考文献

  * Verma, S., 1989: 熱、質量、運動量の移動に対する空気抵抗。地域的な蒸発散の推定において、IAHS Pub, 177, 13-20.
  * Rigden, A., Li, D., Salvucci, G., 2018: 土地被覆タイプにおける摩擦速度に対する熱粗さ長さの依存性: AmeriFlux データを用いた統合分析。農業および森林気象学 249, 512-519.
