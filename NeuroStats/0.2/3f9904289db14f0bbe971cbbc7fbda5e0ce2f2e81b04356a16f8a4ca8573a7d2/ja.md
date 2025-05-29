```
cir(x, y; <キーワード引数>)
```

相関係数の信頼区間を計算します。

# 引数

  * `x::AbstractVector`
  * `y::AbstractVector`
  * `cl::Float64=0.95`: 信頼水準

# 戻り値

  * `cir::Tuple{Float64, Float64}`

```
