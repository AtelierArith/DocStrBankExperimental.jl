```
msci95(s1, s2)
```

平均差、標準偏差、および95%信頼区間を計算します。

# 引数

  * `s1::AbstractArray`
  * `s2::AbstractArray`

# 戻り値

名前付きタプルには以下が含まれます：

  * `sm::Matrix{Float64}`: 平均
  * `ss::Matrix{Float64}`: 標準偏差
  * `su::Matrix{Float64}`: 上側95% CI
  * `sl::Matrix{Float64}`: 下側95% CI
