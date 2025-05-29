```
function watchplots(model = "this"; observe = true, parentSelector::Union{Nothing, AbstractString} = nothing)
```

プロットイベント（例：ポイント選択やホバー）をそれぞれのモデルフィールドに転送するjsスクリプトを生成します。`model`は文字列、モデル、またはモデルタイプであることができます。動的に追加されたプロットもカバーされます。

推奨される使用法は、マウントイベントで呼び出すことです。その場合、モデル引数は省略できます。`Stipple.js_mounted(::Example) = watchplots()`

このアプローチでカバーされるプロットは、少なくとも1つのクラスエントリ `'sync_[prefix]'`（例：`sync_plot`）を含む必要があります。UIプロットノードを生成するために、`plot()`のキーワード引数`syncevents`または`syncprefix`を使用できます：

```
julia> plot("plot.data", syncevents = true)
"<plotly :data="plot.data" :layout="{}" class="sync_plot"></plotly>"

julia> plot("plot.data", syncprefix = "plot1")
"<plotly :data="plot.data" :layout="{}" class="sync_plot1"></plotly>"
```

# 例

```julia
@vars Example begin
    plot::R{Plot} = Plot()
    plot_selected::R{Dict{String, Any}} = Dict{String, Any}()
    plot_hover::R{Dict{String, Any}} = Dict{String, Any}()
    plot1_selected::R{Dict{String, Any}} = Dict{String, Any}()
end

function ui(model::Example)
    page(model, class = "container",
    row(cell(class = "st-module", id = "plotcontainer", [
      # plotlyイベントをフィールドplot_selected、plot_hoverなどに同期します...
      plotly(:plot, syncevents = true),

      # plotlyイベントをフィールドplot1_selected、plot1_hoverなどに同期します...
      plotly(:plot, syncprefix = "plot1", @iif(length(model.plot.data) > 0)),
    ])))
end

Stipple.js_mounted(::Example) = watchplots()

function handlers(model)
  on(model.isready) do isready
      isready || return
      push!(model)
  end

  on(model.plot_selected) do data
      haskey(data, "points") && @info "選択: $(getindex.(data["points"], "pointIndex"))"
  end

  return model
end
```
