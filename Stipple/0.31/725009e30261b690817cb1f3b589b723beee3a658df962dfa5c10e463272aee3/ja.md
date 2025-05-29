```
type ReactiveModel
```

Stippleモデルによって継承される抽象型です。Stippleモデルは、JuliaバックエンドとJavaScript/Vue.jsフロントエンド間の自動双方向データ同期およびデータ交換に使用されます。

### 例

```julia
Base.@kwdef mutable struct HelloPie <: ReactiveModel
  plot_options::R{PlotOptions} = PlotOptions(chart_type=:pie, chart_width=380, chart_animations_enabled=true,
                                            stroke_show = false, labels=["Slice A", "Slice B"])
  piechart::R{Vector{Int}} = [44, 55]
  values::R{String} = join(piechart, ",")
end
```
