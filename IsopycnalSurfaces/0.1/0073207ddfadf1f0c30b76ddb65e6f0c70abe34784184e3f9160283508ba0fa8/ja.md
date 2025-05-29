```
function sigmacolumn(θ,S,p,p0,eos="EOS80")
σ 水柱のための
```

# 引数

  * `θz::Vector{T}`: 潜在温度
  * `Sz::Vector{T}`: 実用塩分
  * `pz::Vector{T}`: 標準圧力の垂直プロファイル
  * `p₀`: 基準圧力
  * `eos:String`: 状態方程式のオプション引数、デフォルト = "EOS80"

# 出力

  * `σ::Vector{T}`: カラム内の湿った点のシグマ
