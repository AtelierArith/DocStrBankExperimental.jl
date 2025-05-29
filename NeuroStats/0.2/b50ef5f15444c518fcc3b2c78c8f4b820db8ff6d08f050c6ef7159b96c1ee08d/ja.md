```
cimd(x; <キーワード引数>)
```

中央値の信頼区間を計算します。

# 引数

  * `x::AbstractArray`
  * `cl::Float64=0.95`: 信頼水準

# 戻り値

  * `cimd::Tuple{Float64, Float64}`
