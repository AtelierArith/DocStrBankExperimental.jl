```
plot_erpimage!(f::Union{GridPosition, GridLayout, Figure}, data::AbstractMatrix{Float64}; kwargs...)
plot_erpimage!(f::Union{GridPosition, GridLayout, Figure}, data::Observable{<:AbstractMatrix}; kwargs...)
plot_erpimage!(f::Union{GridPosition, GridLayout, Figure}, times::Observable{<:AbstractVector}, data::Observable{<:AbstractMatrix{<:Real}}; kwargs...)

plot_erpimage(times::AbstractVector, data::Union{<:Observable{Matrix{<:Real}}, Matrix{<:Real}}; kwargs...)
plot_erpimage(data::Matrix{Float64}; kwargs...)
```

ERP画像をプロットします。

## 引数:

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための `Figure`、`GridLayout`、または `GridPosition`。
  * `data::Union{DataFrame, Vector{Float32}}`   プロットの視覚化のためのデータ。

## キーワード引数 (kwargs)

  * `erpblur::Number = 10`   画像に適用されるぼかしの程度を示す数値。   `ImageFiltering` モジュールのガウスぼかしが使用されます。   非正の値はぼかしを無効にします。
  * `sortvalues::Vector{Int64} = false`   プロットがソートされるパラメータ。Base Juliaの `sortperm()` を使用します。   `sortperm()` は配列のインデックスの順列を計算し、配列をソートされた順序にします。
  * `sortindex::Vector{Int64} = nothing`   インデックス値によるソート。
  * `meanplot::bool = false`   ERP画像の下にデータの平均を示すラインプロットを追加します。
  * `show_sortval::bool = false`   ERP画像の右側にソートデータの分布を示すプロットを追加します。
  * `sortval_xlabel::String = "Sorting variable"`   `show_sortval = true` の場合、x軸ラベルを制御します。
  * `axis.ylabel::String = "Trials"`   `sortvalues = true` の場合、デフォルトのテキストは "Sorted trials" に変更されますが、手動で指定された任意の値に変更できます。
  * `meanplot_axis::NamedTuple = (;)`   ここでmeanplotの設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで `?Axis` と入力してください。   デフォルト: (height = 100, xlabel = "Time", xlabelpadding = 0, xautolimitmargin = (0, 0))
  * `sortplot_axis::NamedTuple = (;)`   ここでmeanplotの設定を柔軟に変更できます。   すべてのオプションを見るには、REPLで `?Axis` と入力してください。   デフォルト: (ylabelvisible = true, yticklabelsvisible = false)

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトが一致するまで循環します。

`;` を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/) の `kwargs...` を使用してください* 

**axis =** (xlabel = "Time", ylabel = "Trials") - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/) の `kwargs...` を使用してください* 

**layout =** (show*legend = true, use*colorbar = true) - *この [ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/) を確認してください* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/) から任意のマッピングを使用してください* 

**visual =** (colormap = Makie.Reverse{String}("RdBu"),) - *[`Makie.heatmap`](https://docs.makie.org/stable/reference/plots/heatmap/) の `kwargs...` を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/) の `kwargs...` を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, label = "Voltage [µV]") - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/) の `kwargs...` を使用してください* 

**戻り値:** ERP画像を表示する `Figure`。 
