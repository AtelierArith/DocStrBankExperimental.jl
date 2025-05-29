```
taylordiagram(S::AbstractArray,C::AbstractArray,names::Vector{String};figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
taylordiagram(S::AbstractArray,C::AbstractArray;figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
taylordiagram(Cs::Union{Vector{Vector{Float64}}, Vector{Vector{Float32}}, Vector{Vector{Float16}}, Vector{Vector{Int64}}}, names::Vector{String};figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
taylordiagram(Cs::Union{Vector{Vector{Float64}}, Vector{Vector{Float32}}, Vector{Vector{Float16}}, Vector{Vector{Int64}}};figsize=600,dpi=600,pointcolor=:black,pointfontsize=8,correlationcolor=:black,freRMS=5)
```

テイラー図を計算してプロットします。関数の異なる4つのバージョンが利用可能です：

  * taylordiagram(S,C,N) は標準偏差 `S` と相関係数 `C` を関連する名前 `N` と共にプロットします
  * taylordiagram(S,C) は標準偏差 `S` と相関係数 `C` を名前 "Obs" と "Mod1..i" と共にプロットします
  * taylordiagram(Cs) はコレクション Cs=[Cr, C1, C2, ...] のためのテイラー図をプロットし、名前 "Obs" と "Mod1..i" を用いて標準偏差と相関係数を計算します
  * taylordiagram(Cs,N) はコレクション Cs=[Cr, C1, C2, ...] のためのテイラー図を関連する名前 `N` と共にプロットし、標準偏差と相関係数を計算します

# オプション

  * `figsize=600` : 図のサイズ
  * `dpi=600` : 図のdpi（ドット毎インチ）
  * `pointcolor=:black` : 散布点の色
  * `pointfontsize=8` : 点の名前のフォントサイズ
  * `correlationcolor=:black` : 相関係数に関連する色（破線、1/4円など）
  * `freRMS=5` : RMSD線の頻度（灰色の円）
  * `normalize=false` : STD正規化
  * `RMSDcolor=:grey` : RMSD線とラベルの色
  * `ang=pi/2` : プロットの角度（例：ang=π/2 の場合、1/4円になります）
  * `std_circ=true` : 標準偏差の目盛り円を表示するかどうか（0を中心に）
  * `rmsd_circ=true` : RMSD円を表示するかどうか（データの標準偏差を中心に）
