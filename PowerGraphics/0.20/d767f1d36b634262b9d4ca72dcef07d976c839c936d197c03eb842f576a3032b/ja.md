```
plot_powerdata!(plot, powerdata)
```

`PowerAnalytics.PowerData`オブジェクトからプロットを作成します。これは、`PowerAnalytics.get_generation_data`の結果のようなものです。

# 引数

  * `plot`: 既存のプロットハンドル、例えば[`plot()`](@extref RecipesBase.plot)の結果（オプション）
  * `powerdata::PowerAnalytics.PowerData`: プロットする`PowerData`オブジェクト

# 受け入れられるキーワード

  * `combine_categories::Bool = false` : カテゴリ値またはカテゴリ内の各値をプロット
  * `curtailment::Bool`: 変数とともにカーテイメントをプロット
  * `set_display::Bool = true`: プロットの表示を防ぐためにfalseに設定
  * `save::String = "file_path"`: プロットを保存するためのファイルパスを設定
  * `format::String = "png"`: [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl))プロットを保存するための異なるフォーマットを設定。オプションには"png"、"pdf"、"eps"が含まれます
  * `seriescolor::Array`: プロットのために異なる色を設定
  * `title::String = "Title"`: プロットのタイトルを設定
  * `stack::Bool = true`: プロットトレースをスタック
  * `bar::Bool` : バープロットを作成
  * `nofill::Bool` : 空の領域の塗りつぶしを強制
  * `stair::Bool`: スタックプロットの代わりに階段プロットを作成
