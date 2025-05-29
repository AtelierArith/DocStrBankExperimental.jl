```
mdiff(s1, s2; <keyword arguments>)
```

2つの信号の平均差と95%信頼区間を計算します。

# 引数

  * `s1::AbstractMatrix`
  * `s2::AbstractMatrix`
  * `n::Int64=3`: ブートストラップの数
  * `method::Symbol=:absdiff`:

      * `:absdiff`: 最大差
      * `:diff2int`: 二乗差の統合面積

# 戻り値

名前付きタプルを含む:

  * `st::Vector{Float64}`
  * `sts::Float64`
  * `p::Float64`
