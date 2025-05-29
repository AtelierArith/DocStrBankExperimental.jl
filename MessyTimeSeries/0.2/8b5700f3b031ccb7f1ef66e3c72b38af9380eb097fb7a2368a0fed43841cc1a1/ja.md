```
artificial_jackknife(Y::Union{FloatMatrix, JMatrix{Float64}}, subsample::Float64, max_samples::Int64, seed::Int64=1)
```

Pellegrino (2022) に従って人工的なジャックナイフサンプルを生成します。

人工的な削除-$d$ジャックナイフは、依存データ問題に対する削除-$d$ジャックナイフの拡張です。

  * この技術は、実際のデータ削除ステップを架空の削除に置き換え、$d$次元の（人工的な）欠測観測パターンをデータに課すことから成ります。
  * このアプローチは、データの順序を変更せず、相関構造を破壊することもありません。

# 引数

  * `Y`: 観測された測定値（`nxT`）、ここで `n` は系列の数、`T` は観測の数です。
  * `subsample`: 元のサンプルサイズのパーセンテージとしての $d$。0 と 1 の間に制約されています。
  * `max_samples`: $\binomial{nT,d}$ が大きすぎる場合、`artificial_jackknife` は `max_samples` のジャックナイフサンプルを生成します。
  * `seed`: ランダムシード（デフォルト: 1）。

# 参考文献

Pellegrino (2022).
