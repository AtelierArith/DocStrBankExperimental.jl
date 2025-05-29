```
plot_glacier_heatmaps(
    results::Results,
    variables::Vector{Symbol},
    title_mapping::Dict;
    scale_text_size::Union{Nothing,Float64}=nothing,
    timeIdx::Union{Nothing,Int64}=nothing
) -> Figure
```

氷河変数のヒートマップをプロットします。

# 引数

  * `results::Results`: プロットするデータを含む結果オブジェクト。
  * `variables::Vector{Symbol}`: プロットする変数のリスト。
  * `title_mapping::Dict`: 変数名をそのタイトルとカラーマップにマッピングする辞書。
  * `scale_text_size::Union{Nothing,Float64}`: テキストサイズをスケールするためのオプション引数。
  * `timeIdx::Union{Nothing,Int64}`: ベクトルの行列を扱う際にデータをプロットするインデックスを選択するためのオプション引数。デフォルトは何も選択されていない状態で、利用可能な最後の要素を選択します。

# 戻り値

  * 氷河のヒートマップのプロット。
