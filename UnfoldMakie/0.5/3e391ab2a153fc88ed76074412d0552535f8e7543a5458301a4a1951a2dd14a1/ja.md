```
plot_topoplot!(f::Union{GridPosition, GridLayout, Figure}, data::Union{<:Observable{<:DataFrame},<:AbstractDataFrame,<:AbstractVector}; positions::Vector, labels = nothing, kwargs...)
plot_topoplot(data::Union{<:Observable{<:DataFrame},<:AbstractDataFrame,<:AbstractVector}; position::Vector, labels = nothing, kwargs...)
```

トポプロットをプロットします。

## 引数

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための `Figure`、`GridLayout`、または `GridPosition`。
  * `data::Union{<:Observable{<:DataFrame},<:AbstractDataFrame,<:AbstractVector}`    プロットの視覚化に使用するデータ。
  * `positions::Vector{Point{2, Float32}}`   `data` が `DataFrame` でない場合に使用される位置。`positions = nothing` の場合、`labels` から位置が生成されます。
  * `labels::Vector{String} = nothing`   `data` が `DataFrame` でない場合に使用されるラベル。
  * `high_chan = nothing` - 色で強調表示するチャネル。
  * `high_color = :darkgreen` - 強調表示用の色。
  * `topo_axis::NamedTuple = (;)`   ここでトポプロット軸の設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで `?Axis` と入力してください。   デフォルト: (width = GridLayoutBase.Relative(1.0f0), height = GridLayoutBase.Relative(1.0f0), halign = 0.05, valign = 0.95, aspect = Makie.DataAspect())
  * `topo_attributes::NamedTuple = (;)`   ここでトポプロットの補間設定を柔軟に変更できます。   すべてのオプションを確認するには、REPLで `?Topoplot.topoplot` と入力してください。   デフォルト: interp_resolution = (128, 128), interpolation = CloughTocher()

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトがサイクルされて一致するまで続きます。

`;` を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/) の `kwargs...` を使用してください* 

**axis =** (xlabel = "Time", aspect = Makie.DataAspect()) - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/) の `kwargs...` を使用してください* 

**layout =** (show*legend = true, use*colorbar = true, hidespines = (), hidedecorations = Dict{Symbol, Bool}(:label => 0)) - *この [ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how_to/hide_deco/) を確認してください* 

**mapping =** (x = nothing, y = (:estimate, :yhat, :y), positions = (:pos, :positions, :position, nothing), labels = (:labels, :label, :sensor, nothing)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/) の任意のマッピングを使用してください* 

**visual =** (colormap = Makie.Reverse{Symbol}(:RdBu), contours = (color = :white, linewidth = 2), enlarge = 1, label*scatter = true, label*text = false, bounding*geometry = GeometryBasics.Circle) - *[`Topoplot.eeg*topoplot`](https://makieorg.github.io/TopoPlots.jl/stable/eeg/) の`kwargs...` を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/) の `kwargs...` を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, flipaxis = true, label = "Voltage [µV]") - *[`Makie.Colorbar`](https://docs.makie.org/stable/reference/blocks/colorbar/) の `kwargs...` を使用してください* 

**戻り値:** トポプロットを表示する `Figure`。
