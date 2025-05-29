```
master(map₁::PolarizedHealpixMap, maskT₁::HealpixMap, maskP₁::HealpixMap,
       map₂::PolarizedHealpixMap, maskT₂::HealpixMap, maskP₂::HealpixMap; already_masked=false)
```

2つの偏光マップに対してモードデカップリング計算を行い、適用するマスクを伴います。$TT$、$TE$、$ET$、$EE$、$EB$、$BE$、および$BB$のスペクトルを返します。

# 引数:

  * `map₁::PolarizedHealpixMap`: 最初のIQUマップ
  * `maskT₁::HealpixMap`: 最初のマップの強度用マスク
  * `maskP₁::HealpixMap`: 最初のマップの偏光用マスク
  * `map₂::PolarizedHealpixMap`: 2番目のIQUマップ
  * `maskT₂::HealpixMap`: 2番目のマップの強度用マスク
  * `maskP₂::HealpixMap`: 2番目のマップの偏光用マスク

# キーワード

  * `already_masked::Bool=false`: 入力マップはすでにマスクと乗算されていますか？
  * `lmin::Int=0`: 最小多極子

# 返り値:

  * `Dict{Symbol,SpectralVector}`: スペクトル `Dict`、`：TT`、`：TE`、`：ET` などでインデックス付けされています。
