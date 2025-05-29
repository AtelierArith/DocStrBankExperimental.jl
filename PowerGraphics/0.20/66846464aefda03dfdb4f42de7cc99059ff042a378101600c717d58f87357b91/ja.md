```
plot_results(results)
```

結果辞書オブジェクトからプロットを作成します

# 引数

  * `results::Dict{String, DataFrame`: プロットする結果

# 受け入れられるキーワード

  * `combine_categories::Bool = false` : カテゴリ値またはカテゴリ内の各値をプロットする
  * `curtailment::Bool`: 変数とともにカーテイルメントをプロットする
  * `set_display::Bool = true`: プロットの表示を防ぐためにfalseに設定
  * `save::String = "file_path"`: プロットを保存するためのファイルパスを設定
  * `format::String = "png"`: [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl)) プロットを保存するための異なるフォーマットを設定。オプションには "png"、"pdf"、"eps" が含まれます
  * `seriescolor::Array`: プロットのために異なる色を設定
  * `title::String = "Title"`: プロットのタイトルを設定
  * `stack::Bool = true`: プロットトレースをスタックする
  * `bar::Bool` : バープロットを作成する
  * `nofill::Bool` : 空の領域の塗りつぶしを強制する
  * `stair::Bool`: スタックプロットの代わりに階段プロットを作成する
