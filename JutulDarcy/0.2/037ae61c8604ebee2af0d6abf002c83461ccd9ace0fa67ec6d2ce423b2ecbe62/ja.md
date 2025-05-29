```
ConstantCompressibilityDensities(
    sys_or_nph::Union{MultiPhaseSystem, Integer},
    reference_pressure = 1.0,
    reference_density = 0.0,
    compressibility = 1.0
)
```

密度の定数圧縮性関係を実装する二次変数。参照圧力、圧縮性、および参照圧力での密度が与えられた場合、各相の密度は次のように計算できます：

$$
ρ(S) = ρ_{ref} e^{(p - p_{ref})c}
$$

コンストラクタは、各相ごとに1つの値を受け取るか、参照条件での参照圧力、圧縮性、および密度のすべての相に対して単一の値を受け取ることができます。

## フィールド

  * `reference_pressure`: 各相の参照圧力（参照密度が与えられる場所）
  * `reference_densities`: 参照点での密度
  * `compressibility`: 参照圧力の周りで拡張する際に使用される圧縮性因子、通常は1e-3と1e-10の間
