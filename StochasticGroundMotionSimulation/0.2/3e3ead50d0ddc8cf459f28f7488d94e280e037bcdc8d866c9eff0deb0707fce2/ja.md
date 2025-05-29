```
near_source_saturation(m, sat::NearSourceSaturationParameters)
```

近接ソース飽和項。等価点ソース距離を作成するために使用されます。`sat.model`に基づいてメソッドを切り替えます。

# 引数

`sat.model`のオプションは次のとおりです：

  * `:BT15` Boore & Thompson (2015) の有限断層係数
  * `:YA15` Yenier & Atkinson (2014) の有限断層係数
  * `:CY14` Chiou & Youngs (2014) の飽和長さにフィットしたモデル（すべての周期にわたる）
  * `:SEA21` Chiou & Youngs (2014) の逆解析から得られたStafford et al. (2021) の飽和モデル
  * `:None` ゼロ飽和長さ
  * `:ConstantConstrained` AD操作の対象とならない定数値 `sat.hconi[1]`
  * `:ConstantVariable` AD操作の対象となる定数値 `sat.hvari[1]`

他のシンボルが渡されると、`NaN`が返されます。

参照： [`near_source_saturation`](@ref)
