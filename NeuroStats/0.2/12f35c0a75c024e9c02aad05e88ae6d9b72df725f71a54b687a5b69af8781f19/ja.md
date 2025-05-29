```
cor_test(seg1, seg2)
```

2つのベクトル間の相関を計算します。

# 引数

  * `s1::AbstractVector`
  * `s2::AbstractVector`

# 戻り値

名前付きタプルを含みます：

  * `t::CorrelationTest{Float64}`
  * `r::Float64`: 相関係数
  * `rc::Tuple{Float64, Float64}`: 相関係数の信頼区間
  * `ts::Tuple{Float64, String}`: t統計量
  * `df::Int64`: 自由度
  * `p::Float64`: p値
