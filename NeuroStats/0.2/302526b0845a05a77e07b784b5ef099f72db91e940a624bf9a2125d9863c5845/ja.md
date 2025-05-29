```
crit_z(alpha; <keyword arguments>)
```

臨界 z スコアを計算します。

# 引数

  * `alpha::Float64=0.05`: アルファ値
  * `twotailed::Bool=true`: 一尾または二尾の確率

# 戻り値

  * `z::Float64`

# 注意事項

一尾の確率のための臨界領域：

  * 左: `(-∞ , -z]`
  * 右: `[z , ∞)`

二尾の確率のための臨界領域: `(-∞ , -z] ∪ [z, ∞)`
