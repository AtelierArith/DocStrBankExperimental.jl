```
Gb_Thom(ustar; constants)
compute_Gb!(df, ::Thom1972)
```

1972年のThomによる境界層伝導率、単純なustar（摩擦速度）依存性に基づく熱伝達のための経験的定式化。

# 引数

  * `ustar`     : 摩擦速度 (m s-1)
  * `df`        : 上記の変数を含むDataFrame
  * `constants=`[`BigleafConstants`](@ref)`()`

# 詳細

Thom 1972によって提案されたRbの経験的方程式は次のとおりです：

$$
Rb = 6.2 {u^*}^{-0.67}
$$

水蒸気と熱のGb（=1/Rb）は、このパッケージでは等しいと仮定されています。

# 値

[`compute_Gb!`](@ref)を参照

# 参考文献

  * Thom, A., 1972: 植生の運動量、質量および熱交換。ロイヤル気象学会の四半期ジャーナル 98, 124-134.
  * Hicks, B*B., Baldocchi, D*D., Meyers, T*P., Hosker, J*R., Matt, D_R., 1987: 測定された量から乾燥沈着速度を導出するための予備的な多重抵抗ルーチン。水、空気、土壌汚染 36, 311-330.

```@example; output = false
using DataFrames
df = DataFrame(ustar = SA[0.1,missing,0.3])
compute_Gb!(df, Thom1972())
propertynames(df) == [:ustar, :Gb_h]
```
