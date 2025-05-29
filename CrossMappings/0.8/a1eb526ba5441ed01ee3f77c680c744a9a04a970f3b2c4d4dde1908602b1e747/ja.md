```
convergentcrossmap(source,
        target,
        timeseries_lengths;
        summarise::Bool = true,
        average_measure::Symbol = :median,
        uncertainty_measure::Symbol = :quantile,
        quantiles = [0.327, 0.673],
        kwargs...)
```

## アルゴリズム

異なる `timeseries_lengths` にわたって `source` シリーズと `target` シリーズの間のクロスマッピングを計算します。 `summarise = true` の場合は `ccm_with_summary` を呼び出します。 `summarise = false` の場合は `ccm` を呼び出します（生のクロスマップスキルを返します）。

## 引数

  * **`source`**: 仮定されるソースプロセスを表すデータシリーズ。
  * **`target`**: 仮定されるターゲットプロセスを表すデータシリーズ。
  * **`timeseries_lengths`**: クロスマッピングを計算するための時間系列の長さ。

## サマリーキーワード引数

  * **`summarise`**: 各時間系列の長さに対してクロスマップスキルを要約すべきですか？ デフォルトは `summarise = true` です。
  * **`average_measure`**: `:median` または `:mean` のいずれか。 デフォルトは `:median` です。
  * **`uncertainty_measure`**: `:quantile` または `:std` のいずれか。 デフォルトは `:quantile` です。
  * **`quantiles`**: `uncertainty_measure` が `:quantile` の場合、量子にわたって不確実性を計算します。 デフォルトは `[0.327, 0.673]` で、通常分布データの1秒に大まかに対応します。

## `crossmap` へのキーワード引数

  * **`dim`**: `target` シリーズから構築された状態空間再構成（遅延埋め込み）の次元。 デフォルトは `dim = 3` です。
  * **`τ`**: `target` から構築された遅延埋め込みの埋め込みラグ。 デフォルトは `τ = 1` です。
  * **`η`**: `target` の遅延埋め込みから `source` のスカラー値を予測する際に使用する予測ラグ。 `η > 0` は前方ラグ（因果的；`source` の過去が `target` の未来に影響を与える）、`η < 0` は後方ラグ（非因果的；`source` の未来が `target` の過去に影響を与える）。 遅延CCMを実行したい場合は予測ラグを調整してください [(Ye et al., 2015)](https://www.nature.com/articles/srep14750)。 デフォルトは `η = 0` で、[Sugihara et al. (2012)](http://science.sciencemag.org/content/early/2012/09/19/science.1227079) と同様です。 *注：ラグ `η` の符号は [TransferEntropy.jl]() の慣習に従うように整理されており、[`rEDM`](https://cran.r-project.org/web/packages/rEDM/index.html) パッケージで使用される慣習とは逆です ([Ye et al., 2016](https://cran.r-project.org/web/packages/rEDM/index.html))。*
  * **`libsize`**: 各クロスマッピングの実現（`n_reps` がある）で、遅延埋め込みポイントから時間インデックスをサンプリングし、最近傍を探すためにいくつのポイントを使用しますか？
  * **`n_reps`**: `target` の遅延埋め込みから `libsize` ポイントのライブラリを何回引き出し、`source` の値を予測しようとしますか？ 同様に、この `libsize` の値で何回クロスマッピングを行いますか？ デフォルトは `n_reps = 100` です。
  * **`replace`**: 遅延埋め込みポイントを置き換えありでサンプリングしますか？ デフォルトは `replace = true` です。
  * **`theiler_window`**: スカラー点 `source(t + η)` を予測するための重みを決定するために、最近傍を探す際に除外する `target_embedding(t)` の遅延埋め込みポイントの時間的隣接点の数。 デフォルトは `theiler_window = 0` です。
  * **`tree_type`**: 最近傍を探す際に構築するツリーのタイプ。 NearestNeighbors.jl のツリータイプでなければなりません。 現在のところ、これは `BruteTree`、`KDTree` または `BallTree` のいずれかです。
  * **`distance_metric`**: Distances.jl の `Metric` のインスタンス。 `BallTree` と `BruteTree` は任意の `Metric` で動作します。 `KDTree` は軸に整列したメトリック `Euclidean`、`Chebyshev`、`Minkowski` および `Cityblock` のみで動作します。 デフォルトは `metric = Euclidean()` *(メトリックのインスタンス化に注意)* です。
  * **`correspondence_measure`**: 実際の `source` の値と予測された値との間の対応を計算する関数。 2つの値のベクトル間の類似度を返す任意の関数にすることができます。 デフォルトは `correspondence_measure = StatsBase.cor` で、$[-1, 1]$ の値を返します。 この場合、負の値は通常フィルタリングされ（ゼロ結合として解釈され）、$1$ の値は完璧な予測を意味します。 [Sugihara et al. (2012)](http://science.sciencemag.org/content/early/2012/09/19/science.1227079) では、平方平均偏差を使用することも提案されており、その場合の値 $0$ は完璧な予測となります。

## 参考文献

Sugihara, George, et al. "Detecting causality in complex ecosystems." Science (2012): 1227079. [http://science.sciencemag.org/content/early/2012/09/19/science.1227079](http://science.sciencemag.org/content/early/2012/09/19/science.1227079)

Ye, Hao, et al. "Distinguishing time-delayed causal interactions using convergent cross mapping." Scientific Reports 5 (2015): 14750. [https://www.nature.com/articles/srep14750](https://www.nature.com/articles/srep14750)

Ye, H., et al. "rEDM: Applications of empirical dynamic modeling from time series." R Package Version 0.4 7 (2016). [https://cran.r-project.org/web/packages/rEDM/index.html](https://cran.r-project.org/web/packages/rEDM/index.html)
