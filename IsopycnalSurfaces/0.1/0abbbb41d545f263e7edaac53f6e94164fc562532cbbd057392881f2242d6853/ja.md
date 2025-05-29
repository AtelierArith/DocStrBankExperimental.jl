```
function vars2sigma(vars,p,p₀,σgrid;spline_order,linearinterp,eos)
正規の3Dグリッドからシグマ面への変数をマップします
```

# 引数

  * `vars::Dict{String,Array{T,3}}}`: 3D配列の辞書
  * `p::Vector{T}`: 標準圧力の垂直プロファイル
  * `p₀`: 参照圧力
  * `σgrid`: σ面の値
  * `splorder`: 1-5、スプラインの次数、オプションのキーワード引数、デフォルト=3
  * `linearinterp`: オプションのキーワード論理引数、デフォルト=false
  * `eos`: 状態方程式のためのオプションのキーワード文字列、デフォルト = "EOS80"

# 出力

  * `varsσ::Dict{String,Array{T,3}`: シグマ1面上の変数の3D配列の辞書
