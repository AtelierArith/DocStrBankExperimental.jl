```
linear(xdata, ydata, x::Number)
```

線形補間。

**引数**

  * `xdata::Vector{Float64}`: 補間を構築するために使用されるxデータ
  * `ydata::Vector{Float64}`: 補間を構築するために使用されるyデータ
  * `x::Float64`: スプラインを評価する点

**戻り値**

  * `y::Float64`: 線形補間を使用してxでの値
