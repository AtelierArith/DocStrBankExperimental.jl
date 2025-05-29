```
compute_Gb_quantities(Gb_h)
compute_Gb_quantities!(df:::AbstractDataFrame)
```

熱の境界層伝導率に基づいて、導出された量を計算します。

# 引数

  * `Gb_h` : 熱伝達のための境界層伝導率 (m s-1)
  * `df`   : 上記の列を持つDataFrame
  * `constants=`[`BigleafConstants`](@ref)`()`: エントリ `Sc_CO2` と `Pr`

# 値

エントリを持つNamedTuple

  * `Gb_h`: 熱伝達のための境界層伝導率 (m s-1)
  * `Rb_h`: 熱伝達のための境界層抵抗 (s m-1)
  * `kB_h`: 熱伝達のためのkB^(-1)パラメータ
  * `Gb_CO2`: CO2のための境界層伝導率 (m s-1).
