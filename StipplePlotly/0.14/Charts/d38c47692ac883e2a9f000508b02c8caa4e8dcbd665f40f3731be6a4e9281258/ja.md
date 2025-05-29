```
plot(data::Union{Symbol,AbstractString}, args...;
  layout::Union{Symbol,AbstractString,LayoutType} = Charts.PlotLayout(),
  config::Union{Symbol,AbstractString,Nothing,ConfigType} = nothing, configtype = Charts.PlotConfig,
  syncevents::Bool = false, syncprefix = "", class = "", keepselection::Bool = false, kwargs...) :: String  where {LayoutType, ConfigType}
```

与えられたデータと引数を使用してplotlyプロットを生成します。パラメータ：

  * `data::Union{Symbol,AbstractString}`: プロットデータを保持するフィールドの名前
  * `layout::Union{Symbol,AbstractString,LayoutType}`: プロットのレイアウト。デフォルト: `Charts.PlotLayout()`
  * `config::Union{Symbol,AbstractString,Nothing,ConfigType}`: プロットの設定。デフォルト: `nothing`
  * `configtype::ConfigType`: 設定のタイプ。デフォルト: `Charts.PlotConfig`
  * `syncevents::Bool`: イベントを同期するかどうか。デフォルト: `false`
  * `syncprefix::String`: 同期はプロットのクラス属性を介して制御されます。空のままにすると、クラスはデータ名から派生します。
  * `class::String`: プロットの追加クラス属性
  * `args`: さらなるカスタム引数
  * `kwargs`: さらなるカスタムキーワード引数

plotlyイベントの転送は、`syncevents`を`true`に設定するか、`syncprefix`を提供することで実現されます。イベントが転送されるモデルフィールドは、`syncprefix`とイベントタイプから派生します。例えば、`syncprefix = "myplot"`は`plotly_selected`イベントを`myplot_selected`モデルフィールドに転送します。最も一般的なイベントタイプは`plotly_selected`、`plotly_hover`、`plotly_click`、および`plotly_relayout`であり、これらは`@mixin myplot::PBPlotWithEvents`を介してモデルに含めることができます。

イベント転送の例は、StipplePlotlyのドキュメント文字列にあります。
