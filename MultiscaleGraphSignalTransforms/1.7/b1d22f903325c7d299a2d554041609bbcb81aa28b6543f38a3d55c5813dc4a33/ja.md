```
scatter_gplot(X; marker = nothing, ms = 4, plotOrder = :normal, c = :viridis, subplot = 1)
```

SCATTER*GPLOTは、グラフ信号を迅速に表示するための散布図を生成します。SCATTER*GPLOT!(X; ...)は、`current`のプロットに追加します。

# 入力引数

  * `X::Matrix{Float64}`: 点の位置、2次元または3次元であることができます。
  * `marker::Array{Float64}`: デフォルトは`nothing`です。各ノードで異なる信号値に応じて異なる色を表示します。
  * `ms::Array{Float64}`: デフォルトは`4`です。各ノードで異なる信号値に応じて異なるノードサイズを表示します。
  * `shape::Symbol`: デフォルトは`:none`です。マーカーの形状。
  * `mswidth::Number`: デフォルトは`0`です。マーカーのストロークボーダーの幅。
  * `msalpha::Number`: デフォルトは`nothing`です。マーカーのストロークの不透明度。
  * `plotOrder::Symbol`: デフォルトは`:normal`です。オプションの選択肢は`:s2l`または`:l2s`、すなわち、`marker`の最小値から最大値までプロットするか、その逆、または`:propabs`、msがマーカー値の絶対値に比例するように自動的に設定されます。
  * `c::Symbol`: デフォルトは`:viridis`です。マーカーの色。
  * `subgplot::Int`: デフォルトは`1`です。サブプロットのインデックス。
