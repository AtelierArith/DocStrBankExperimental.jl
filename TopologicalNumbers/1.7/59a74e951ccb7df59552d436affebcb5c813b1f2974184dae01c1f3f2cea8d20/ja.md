```
plot2D(nums::T1, param_range1::T2, param_range2::T3; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram") where {T1<:AbstractArray,T2<:AbstractVector,T3<:AbstractVector}
```

2D相図をプロットします。

# 引数

  * `nums::T1`: 相図を表す数値の配列。
  * `param_range1::T2`: 最初のパラメータの範囲を表すベクトル。
  * `param_range2::T3`: 2番目のパラメータの範囲を表すベクトル。
  * `labels::Bool=true`: 軸ラベルを表示するかどうか。デフォルトは`true`。
  * `disp::Bool=true`: プロットを表示するかどうか。デフォルトは`true`。
  * `png::Bool=false`: プロットをPNGファイルとして保存するかどうか。デフォルトは`false`。
  * `pdf::Bool=false`: プロットをPDFファイルとして保存するかどうか。デフォルトは`false`。
  * `svg::Bool=false`: プロットをSVGファイルとして保存するかどうか。デフォルトは`false`。
  * `filename::String="phaseDiagram"`: 保存するプロットのファイル名。デフォルトは"phaseDiagram"。

# 戻り値

  * `fig`: matplotlibのフィギュアオブジェクト。

# 例

```julia
julia>
```
