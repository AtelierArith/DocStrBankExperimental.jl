```
plot_glacier_integrated_volume(
    results,
    variables,
    title_mapping;
    tspan,
    figsize::Union{Nothing, Tuple{Int64, Int64}}=nothing,
)

氷河の変数の統合体積を時間にわたってプロットします。

# 引数

  * `results::Results`: プロットするデータを含む結果オブジェクト。
  * `variables::Vector{Symbol}`: プロットする変数。
  * `title_mapping`: 変数名をそのタイトルにマッピングする辞書。
  * `tspan`: シミュレーションの開始時刻と終了時刻を表すタプル。
  * `figsize::Union{Nothing, Tuple{Int64, Int64}}`: 図のサイズ。

# 戻り値

  * 氷河の統合体積のプロット。
```
