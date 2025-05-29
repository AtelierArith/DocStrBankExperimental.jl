```
plotx(X, Y...; xlabel="時間 [s]", ylabels=nothing, labels=nothing, xlims=nothing, ylims=nothing, ann=nothing, 
           scatter=false, title="", fig="", title="", ysize=14, yzoom=1.0, disp=false)
```

複数のy軸と1つのx軸を持つオシロスコープのようなプロットを作成します。

# 引数

  * `X::Vector`: x軸データ
  * `Y::Vector`: カンマ区切りの任意の数のy軸ベクトル
  * `xlabel::String`: x軸ラベル
  * `ylabels::Vector{String}`: y軸ラベル
  * `labels::Vector{String}`: 各y軸のラベル
  * `xlims::Tuple{Float64, Float64}`: x軸の制限
  * `ylims::Tuple{Float64, Float64}`: y軸の制限
  * `ann::Vector{Tuple{Float64, Float64, String}}`: 注釈
  * `scatter::Bool`: 散布図
  * `fig::String`: 図の名前
  * `title::String`: タイトル
  * `ysize::Int`: y軸ラベルのサイズ
  * `yzoom::Float64`: y軸ズーム係数
  * `disp::Bool`: プロットを表示するか、単にPlotX構造体を返すか
