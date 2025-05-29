```
function plotly(p::Symbol; layout = Symbol(p, ".layout"), config = Symbol(p, ".config"), configtype = default_config_type(), keepselection = false, kwargs...)
```

これは、PlotlyBase.Plotまたはdata、layout、configフィールドを持つ構造体をレンダリングするための便利な関数です。

# 例

```julia
julia> plotly(:plot)
"<plotly :data="plot.data" :layout="plot.layout" :config="plot.config"></plotly>"
```

共通のconfigまたはlayoutを持つ複数のプロットの典型的な使用法は次のとおりです。

```julia
julia> plotly(:plot, config = :config)
"<plotly :data="plot.data" :layout="plot.layout" :config="config"></plotly>"
```
