```
mdiff(s1, s2; <keyword arguments>)
```

チャネル間の平均差とその95% CIを計算します。

# 引数

  * `s1::AbstractArray`
  * `s2::AbstractArray`
  * `n::Int64=3`: ブートストラップの数
  * `method::Symbol=:absdiff`

      * `:absdiff`: 最大差
      * `:diff2int`: 二乗差の統合面積

# 戻り値

名前付きタプルを含む:

  * `st::Matrix{Float64}`
  * `sts::Vector{Float64}`
  * `p::Vector{Float64}`
