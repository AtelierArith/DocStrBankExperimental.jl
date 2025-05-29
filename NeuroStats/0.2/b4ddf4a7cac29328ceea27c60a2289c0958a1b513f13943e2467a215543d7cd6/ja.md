```
crit_t(df, alpha; <keyword arguments>)
```

臨界t値を計算します。

# 引数

  * `df::Real`: 自由度（通常 df = n - 1）
  * `alpha::Float64=0.05`: アルファ値
  * `twotailed::Bool=true`: 一尾または二尾の確率

# 戻り値

  * `t::Float64`

# 注意事項

一尾の確率のための臨界領域：

  * 左: `(-∞ , -t]`
  * 右: `[t , ∞)`

二尾の確率のための臨界領域: `(-∞ , -t] ∪ [t, ∞)`
