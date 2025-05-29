2023年12月に作成された [chifi - an open source software dynasty.](https://github.com/orgs/ChifiSource)

  * このソフトウェアはMITライセンスです。

### Gattino

`Gattino` は、`Toolips` ウェブ開発フレームワークのHTMLテンプレート（`ToolipsSVG`）を使用して構築された、Julia用の**ハイパーコンポーザブル**SVGビジュアライゼーションライブラリです。使用は、データをスケーラブルベクターグラフィックスに変換し、ウィンドウにスケールするために提供される `Context` を中心に展開されます。 `Context` は通常、`context` 関数を介して作成されます：

```julia
mycon = context(200, 200) do con::Context
    text!(con, 250, 250, "hello world!")
    points!(con, [1, 2, 3, 4], [1, 2, 3, 4])
end
```

`Gattino`

  * ビジュアライゼーションの作成と編集に関する詳細は、`?context` を使用してください。

###### names

  * **colors**（エクスポートされていません）

```julia
randcolor
make_gradient
```

  * **visualizations**（エクスポートされています）

```julia
# plot   | context plotting equivalent
scatter #| scatter_plot!
line    #| line_plot!
hist    #| hist_plot!
```

  * **contexts**（エクスポートされています）

```julia
AbstractContext
vcat(comp::AbstractContext, cons::AbstractContext ...)
hcat(comp::AbstractContext, cons::AbstractContext ...)
vcat(comp::Component{:div}, cons::AbstractContext ...)
hcat(comp::Component{:div}, cons::AbstractContext ...)
Context
context
layers
draw!
Group
group
group!
style!(con::AbstractContext, s::String, spairs::Pair{String, String} ...)
ToolipsServables.animate!(con::AbstractContext, layer::String, animation::ToolipsSVG.KeyFrames)
merge!(c::AbstractContext, c2::AbstractContext)
delete_layer!
rename_layer!
move_layer!
set_shape!
open_layer!
set!
set_gradient!
style!(ecomp::Pair{Int64, <:ToolipsSVG.ToolipsServables.AbstractComponent}, vec::Vector{<:Number}, stylep::Pair{String, Int64} ...)
compress!
```

  * **context plotting**（エクスポートされていません）

```julia
text!
line!
gridlabels!
grid!
labeled_grid!
points!
axes!
axislabels!
bars!
barlabels!
v_bars!
v_barlabels!
legend!
append_legend!
make_legend_preview
```
