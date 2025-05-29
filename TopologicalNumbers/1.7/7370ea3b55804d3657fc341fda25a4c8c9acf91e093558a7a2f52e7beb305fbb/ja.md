```
plot1D(nums::T1, param_range::T2; labels::Bool=true, disp::Bool=true, png::Bool=false, pdf::Bool=false, svg::Bool=false, filename::String="phaseDiagram") where {T1<:AbstractMatrix,T2<:AbstractVector}
```

1Dフェーズダイアグラムをプロットします。

# 引数

  * `nums::T1`: プロットするデータを含む行列またはベクトル。
  * `param_range::T2`: パラメータ範囲を表すベクトル。
  * `labels::Bool=true`: 軸ラベルを表示するかどうか。デフォルトは`true`。
  * `disp::Bool=true`: プロットを表示するかどうか。デフォルトは`true`。
  * `png::Bool=false`: プロットをPNGファイルとして保存するかどうか。デフォルトは`false`。
  * `pdf::Bool=false`: プロットをPDFファイルとして保存するかどうか。デフォルトは`false`。
  * `svg::Bool=false`: プロットをSVGファイルとして保存するかどうか。デフォルトは`false`。
  * `filename::String="phaseDiagram"`: 保存するプロットのファイル名。デフォルトは"phaseDiagram"。

# 例

```julia
nums = [1 2 3; 4 5 6]
param_range = [0.1, 0.2, 0.3]
plot1D(nums, param_range)
```

# 戻り値

  * `fig`: プロットを表すmatplotlibのフィギュアオブジェクト。
