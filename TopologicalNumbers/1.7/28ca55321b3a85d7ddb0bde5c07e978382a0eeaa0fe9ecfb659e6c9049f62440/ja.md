```
plot2D(result::NamedTuple; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram")
```

2D相図をプロットします。

# 引数

  * `result::NamedTuple`: 結果データを含む名前付きタプル。
  * `labels::Bool=true`: 軸ラベルを表示するかどうか。
  * `disp::Bool=true`: プロットを表示するかどうか。
  * `png::Bool=false`: プロットをPNGファイルとして保存するかどうか。
  * `pdf::Bool=false`: プロットをPDFファイルとして保存するかどうか。
  * `svg::Bool=false`: プロットをSVGファイルとして保存するかどうか。
  * `filename::String="phaseDiagram"`: 保存するプロットのファイル名。

# 戻り値

  * `fig`: matplotlibのフィギュアオブジェクト。

# 例

```julia
julia>
```
