```
plot1D(::T1, nums::T2, param_range::T3; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram") where {T1<:SecondChernAlgorithms,T2<:AbstractVector,T3<:AbstractVector}
```

1D位相図をプロットします。

# 引数

  * `::T1`: `SecondChernAlgorithms`インターフェースを実装するタイプ`T1`のオブジェクト。
  * `nums::T2`: プロットする値を表す数のベクトル。
  * `param_range::T3`: パラメータ範囲を表すベクトル。
  * `labels::Bool=true`: プロットにラベルを表示するかどうか。デフォルトは`true`。
  * `disp::Bool=true`: プロットを表示するかどうか。デフォルトは`true`。
  * `png::Bool=false`: プロットをPNGファイルとして保存するかどうか。デフォルトは`false`。
  * `pdf::Bool=false`: プロットをPDFファイルとして保存するかどうか。デフォルトは`false`。
  * `svg::Bool=false`: プロットをSVGファイルとして保存するかどうか。デフォルトは`false`。
  * `filename::String="phaseDiagram"`: 保存されたプロットのファイル名。デフォルトは`"phaseDiagram"`。

# 例

```julia
plot1D(obj, nums, param_range)
```

# 戻り値

  * `fig`: プロットを表すmatplotlibフィギュアオブジェクト。
