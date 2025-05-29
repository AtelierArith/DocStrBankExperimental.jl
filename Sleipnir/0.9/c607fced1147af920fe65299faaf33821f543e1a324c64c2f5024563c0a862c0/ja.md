```
plot_glacier_statistics_evolution(
    results::Results,
    variables::Vector{Symbol},
    title_mapping;
    metrics="median",
    tspan,
    threshold=0.5,
    figsize::Union{Nothing, Tuple{Int64, Int64}}=nothing,
)
```

複数の氷河変数の統計の進化を時間にわたってプロットします。

# 引数

  * `results::Results`: プロットするデータを含むシミュレーション結果オブジェクト。
  * `variables::Vector{Symbol}`: プロットする変数のリスト。
  * `title_mapping`: 変数名をそのタイトルにマッピングする辞書。
  * `metrics`: 可視化するメトリクス、例："average"、"median"、"min"、"max"、および "std"。デフォルトは "median"。
  * `tspan`: シミュレーションの開始時刻と終了時刻を表すタプル。
  * `threshold`: データをフィルタリングするための閾値。デフォルトは 0.5。
  * `figsize::Union{Nothing, Tuple{Int64, Int64}}`: 図のサイズ。

# 戻り値

  * 氷河統計の進化のプロット。
