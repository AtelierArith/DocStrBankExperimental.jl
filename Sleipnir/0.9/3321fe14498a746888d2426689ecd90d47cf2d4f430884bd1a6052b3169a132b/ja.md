```
plot_glacier(results::Results, plot_type::String, variables::Vector{Symbol}; kwargs...) -> Figure
```

氷河データのさまざまなタイプのプロットを生成します。

# 引数

  * `results::Results`: プロットするデータを含む結果オブジェクト。
  * `plot_type::String`: 生成するプロットのタイプ。オプションは次のとおりです：

      * "heatmaps": `:H`、`:H₀`、`:S`、`:B`、`:V`、`:Vx`、`:Vy`、`:V_ref`などの氷河変数のヒートマップ。
      * "evolution difference": 変数の時間的差分指標（開始と終了の間）で、オプションの指標として "hist"（ヒストグラム）や "difference"。
      * "evolution statistics": 変数の時間的統計指標で、オプションの指標として "average"、"median"、"min"、"max"、"std"。
      * "integrated volume": 変数の統合された氷の体積の時間的進化。
      * "bias": 2つの変数間のバイアスを視覚化する散布図。
  * `variables::Vector{Symbol}`: プロットする変数、例： `:H`。

# オプションのキーワード引数

  * `tspan`: シミュレーションの開始時刻と終了時刻を表すタプル。
  * `metrics`: 可視化する指標、例：統計のための `["average"]`、差分のための `["difference"]`。
  * `scale_text_size::Union{Nothing,Float64}`: ヒートマップのテキストサイズをスケーリングするためのオプション引数。
  * `threshold::Vector{F}`: バイアスプロットでデータをフィルタリングするための閾値。
  * `figsize::Tuple{Int64, Int64}`: 図のサイズ。

# 戻り値

  * 希望する視覚化を含む `Figure` オブジェクト。

# 注意事項

  * `variables` と `kwargs` が指定された `plot_type` の要件に一致することを確認してください。
  * この関数は、`plot_type` に基づいて特定のプロット関数にリクエストをルーティングします。

```
