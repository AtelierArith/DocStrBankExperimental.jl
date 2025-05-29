```
plot_erp!(f::Union{GridPosition, GridLayout, Figure}, plot_data::Union{DataFrame, AbstractMatrix, AbstractVector{<:Number}}; kwargs...)
plot_erp(times, plot_data::Union{DataFrame, AbstractMatrix, AbstractVector{<:Number}}; kwargs...)
```

ERPプロットを描画します。   

## 引数

  * `f::Union{GridPosition, GridLayout, Figure}`   プロットを描画するための`Figure`、`GridLayout`、または`GridPosition`。
  * `data::Union{Union{DataFrame, AbstractMatrix, AbstractVector{<:Number}, Vector{Float32}}`   ERPプロットの視覚化のためのデータ。
  * `kwargs...`   追加のスタイリング動作。    よく使われる例: `plot_erp(df; mapping = (; color = :coefname, col = :conditionA))`。

## キーワード引数 (kwargs)

  * `stderror::Bool = false`   `:stderror`列に基づいて下限と上限を持つエラリボンを追加します。
  * `significance::DataFrame = nothing`   有意な時間帯を水平バーとして表示します。   例: `DataFrame(from = [0.1, 0.3], to = [0.5, 0.7], coefname = ["(Intercept)", "condition: face"])`。   `coefname`が指定されていない場合、有意性の線は黒になります。
  * `layout.use_colorbar = true`   カラーバーを有効または無効にします。
  * `layout.use_legend = true`   凡例を有効または無効にします。
  * `layout.show_legend = true`   凡例とカラーバーを有効または無効にします。
  * `mapping = (;)`   `color`、`col`（列）、`linestyle`、`group`を指定します。   例: `mapping = (; col = :group)`は各グループのための列を作成します。
  * `visual = (; color = Makie.wong_colors, colormap = :roma)`   カテゴリカルカラーには`visual.color`を、連続的なものには`visual.colormap`を使用します。

## 共有プロット設定オプション

共有プロットオプションは次のように使用できます: `type = (; key = value, ...))`。 例えば、`plot_x(...; colorbar = (; vertical = true, label = "Test"))`。 複数のデフォルトが一致するまで循環します。

`;`を置くことが重要です！

**figure =** NamedTuple() - *[`Makie.Figure`](https://docs.makie.org/stable/explanations/figure/)の`kwargs...`を使用してください* 

**axis =** (xlabel = "時間", ylabel = "電圧 [µV]", yticklabelsize = 14, xtickformat = "{:.1f}") - *[`Makie.Axis`](https://docs.makie.org/stable/reference/blocks/axis/)の`kwargs...`を使用してください* 

**layout =** (show*legend = true, use*colorbar = true, use*legend = true, hidespines = (:r, :t), hidedecorations = Dict{Symbol, Bool}(:grid => 1, :label => 0, :ticks => 0, :ticklabels => 0)) - *この[ページ](https://unfoldtoolbox.github.io/UnfoldMakie.jl/dev/generated/how*to/hide_deco/)を確認してください* 

**mapping =** (x = (:time,), y = (:estimate, :yhat, :y), color = (:color, :coefname, nothing)) - *[`AlgebraOfGraphics`](https://aog.makie.org/stable/layers/mapping/)の任意のマッピングを使用してください* 

**visual =** (colormap = :roma, color = ColorTypes.RGBA{Float32}[RGBA(0.0, 0.44705883, 0.69803923, 1.0), RGBA(0.9019608, 0.62352943, 0.0, 1.0), RGBA(0.0, 0.61960787, 0.4509804, 1.0), RGBA(0.8, 0.4745098, 0.654902, 1.0), RGBA(0.3372549, 0.7058824, 0.9137255, 1.0), RGBA(0.8352941, 0.36862746, 0.0, 1.0), RGBA(0.9411765, 0.89411765, 0.25882354, 1.0)]) - *[`Makie.lines`](https://docs.makie.org/stable/reference/plots/lines/)の`kwargs...`を使用してください* 

**legend =** (orientation = :vertical, tellwidth = true, tellheight = false, halign = :right, valign = :center, framevisible = false) - *[`Makie.Legend`](https://docs.makie.org/stable/reference/blocks/legend/)の`kwargs...`を使用してください* 

**colorbar =** (vertical = true, tellwidth = true, tellheight = false, labelrotation = -1.5707963267948966, label = "", flipaxis = true) - *[`AlgebraOfGraphics.colorbar!`](@ref)の`kwargs...`を使用してください* 

**戻り値:** ERPプロットを表示する`Figure`。
