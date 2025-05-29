```
plot_glacier_difference_evolution(
    results::Results,
    variables::Vector{Symbol},
    title_mapping;
    tspan::Tuple{F,F}=results.tspan,
    metrics::Vector{String}="difference",
    figsize::Union{Nothing, Tuple{Int64, Int64}}=nothing,
) where {F<:AbstractFloat}
```

氷河の変数の差の進化を時間にわたってプロットします。

# 引数

  * `results::Results`: プロットするデータを含むシミュレーション結果オブジェクト。
  * `variables::Vector{Symbol}`: プロットする変数。
  * `title_mapping`: 変数名をそのタイトルにマッピングする辞書。
  * `tspan::Tuple{F,F}`: シミュレーションの開始時刻と終了時刻を表すタプル。
  * `metrics::Vector{String}`: 可視化するメトリクス、例: `["difference"]`。
  * `figsize::Union{Nothing, Tuple{Int64, Int64}}`: 図のサイズ。

# 戻り値

  * 氷河の差の進化のプロット。
