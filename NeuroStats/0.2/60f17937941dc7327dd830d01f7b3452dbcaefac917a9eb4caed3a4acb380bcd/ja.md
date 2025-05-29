```
msci95(s1, s2)
```

平均差、標準偏差、および95%信頼区間を計算します。

# 引数

  * `s1::AbstractVector`
  * `s2::AbstractVector`

# 戻り値

名前付きタプルを含みます：

  * `sm::Float64`: 平均
  * `ss::Float64`: 標準偏差
  * `su::Float64`: 上限95% CI
  * `sl::Float64`: 下限95% CI
