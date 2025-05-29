```
add_arrows!(plt::PlotlyJS.SyncPlot, origin::Vector{<:Real}, dir::Vector{<:Real}, len::Real=1.0, color::String=""; opc::Real=1, endpoint::Bool=true, asize::Real=len)

指定された方向に向かって点から始まる3D矢印を作成します。

# 引数
- `plt::PlotlyJS.SyncPlot`: 軸が追加されるプロット。
- `origin::Vector{<:Real}`: 矢印の始点。
- `dir::Vector{<:Real}`: 矢印の方向ベクトル。
- `len::Real`: 矢印の長さ
- `color::String`: 矢印の色。

# キーワード
- `opc`: 矢印の不透明度。デフォルトは1。
- `asize` 矢印のコーンのサイズ係数。デフォルトは`len`。
```
