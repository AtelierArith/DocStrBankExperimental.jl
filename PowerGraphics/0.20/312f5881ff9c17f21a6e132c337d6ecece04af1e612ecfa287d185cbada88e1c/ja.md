```
plot_dataframe!(plot, df)
plot_dataframe!(plot, df, time_range)
```

[`DataFrames.DataFrame`](@extref) からデータをプロットします。各行は時間の期間を表し、各列はトレースを表します。

# 引数

  * `plot`: 既存のプロットハンドル、例えば [`plot()`](@extref RecipesBase.plot) の結果
  * `df::DataFrames.DataFrame`: 各行が時間の期間を表し、各列がトレースを表す `DataFrame`。

`DataFrame` のみが提供される場合、`DateTime` 値の列が必要です。

  * `time_range::Union{DataFrames.DataFrame, Array, StepRange}`: データの時間の期間

# 受け入れられるキーワード

  * `curtailment::Bool`: 変数とともにカーテイメントをプロット
  * `set_display::Bool = true`: プロットの表示を防ぐために false に設定
  * `save::String = "file_path"`: プロットを保存するためのファイルパスを設定
  * `format::String = "png"`: [PlotlyJS](@extref Plots [Plotly-/-PlotlyJS](https://github.com/spencerlyon2/PlotlyJS.jl)) プロットを保存するための異なるフォーマットを設定。オプションには "png"、"pdf"、"eps" が含まれます
  * `seriescolor::Array`: プロットの異なる色を設定
  * `title::String = "Title"`: プロットのタイトルを設定
  * `stack::Bool = true`: プロットトレースをスタック
  * `bar::Bool` : バープロットを作成
  * `nofill::Bool` : 空の領域の塗りつぶしを強制
  * `stair::Bool`: スタックプロットの代わりに階段プロットを作成
