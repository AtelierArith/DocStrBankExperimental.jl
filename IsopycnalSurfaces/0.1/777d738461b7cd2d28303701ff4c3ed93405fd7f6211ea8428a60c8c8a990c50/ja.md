```
function var2sigmacolumn(σ,v,σgrid;splorder,linearinterp)
水柱のσ₁面にθ,S,pをマッピングする
```

# 引数

  * `σ`::Array{Float,1}}`: 入力変数のシグマ値
  * `v::Array{Float,1}}`: 興味のある変数
  * `σgrid`: σ面の値
  * `splorder`: 1-5のオプション引数、スプラインの次数、デフォルト=3
  * `linearinterp`: オプション引数、線形補間を強制する場合はtrue、デフォルト=false

# 出力

  * `θonσ`: シグマ面上の変数
