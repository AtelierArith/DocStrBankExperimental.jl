```
function vars2sigma2(vars,p,σgrid;spline_order,linearinterp,eos)
正規の3Dグリッドからσ₂面に変数をマップします
```

# 引数

  * `vars::Dict{String,Array{T,3}}}`: 3D配列の辞書
  * `p::Vector{T}`: 標準圧力の垂直プロファイル
  * `σgrid`: σ面の値
  * `splorder`: 1-5、スプラインの次数、オプションのキーワード引数、デフォルト=3
  * `linearinterp`: オプションのキーワード論理引数、デフォルト=false
  * `eos`: 状態方程式のためのオプションのキーワード文字列、デフォルト = "EOS80"

# 出力

  * `varsσ::Dict{String,Array{T,3}`: sigma1面上の変数の3D配列の辞書
