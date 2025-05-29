```
ccm(source,
        target,
        timeseries_lengths;
        kwargs...) -> Vector{Vector{Float64}}
```

## アルゴリズム

異なる `timeseries_lengths` にわたって `source` シリーズと `target` シリーズの間のクロスマッピングを計算します。

## 引数

  * **`source`**: 仮定されるソースプロセスを表すデータシリーズ。
  * **`target`**: 仮定されるターゲットプロセスを表すデータシリーズ。
  * **`timeseries_lengths`**: クロスマッピングを計算するための時間系列の長さ。

## `crossmap` へのキーワード引数

  * **`dim`**: `target` シリーズから構築された状態空間再構成（遅延埋め込み）の次元。デフォルトは `dim = 3`。
  * **`τ`**: `target` から構築された遅延埋め込みの埋め込みラグ。デフォルトは `τ = 1`。
  * **`η`**: `target` の遅延埋め込みから `source` のスカラー値を予測する際に使用する予測ラグ。`η > 0` は前方ラグ（因果的；`source` の過去が `target` の未来に影響を与える）、`η < 0` は後方ラグ（非因果的；`source` の未来が `target` の過去に影響を与える）。遅延した ccm を実行したい場合は、予測ラグを調整してください [(Ye et al., 2015)](https://www.nature.com/articles/srep14750)。デフォルトは `η = 0` で、[Sugihara et al. (2012)](http://science.sciencemag.org/content/early/2012/09/19/science.1227079) と同様です。*注：ラグ `η` の符号は [TransferEntropy.jl]() の慣習に従うように整理されており、[`rEDM`](https://cran.r-project.org/web/packages/rEDM/index.html) パッケージで使用される慣習とは逆です ([Ye et al., 2016](https://cran.r-project.org/web/packages/rEDM/index.html))。*
  * **`libsize`**: 各クロスマッピングの実現（`n_reps` がある）で、遅延埋め込みポイントから時間インデックスをサンプリングし、最近傍を探すために使用する遅延埋め込みポイントの数は？
  * **`n_reps`**: `target` の遅延埋め込みから `libsize` ポイントのライブラリを引き出し、`source` の値を予測しようとする回数。言い換えれば、この `libsize` の値でクロスマッピングを行う回数は？デフォルトは `n_reps = 100`。
  * **`replace`**: 遅延埋め込みポイントを置き換えありでサンプリングしますか？デフォルトは `replace = true`。
  * **`theiler_window`**: スカラー点 `source(t + η)` を予測するための重みを決定する際に、最近傍を探すときに除外する `target_embedding(t)` の遅延埋め込みポイントの時間的隣接点の数。デフォルトは `theiler_window = 0`。
  * **`tree_type`**: 最近傍を探す際に構築するツリーのタイプ。NearestNeighbors.jl のツリータイプでなければなりません。現時点では、`BruteTree`、`KDTree`、または `BallTree` のいずれかです。
  * **`distance_metric`**: Distances.jl の `Metric` のインスタンス。`BallTree` と `BruteTree` は任意の `Metric` で動作します。`KDTree` は軸に整列したメトリック `Euclidean`、`Chebyshev`、`Minkowski`、および `Cityblock` のみで動作します。デフォルトは `metric = Euclidean()` *(メトリックのインスタンス化に注意)*。
  * **`correspondence_measure`**: `source` の実際の値と予測された値の間の対応を計算する関数。2つの値のベクトル間の類似度を返す任意の関数を使用できます。デフォルトは `correspondence_measure = StatsBase.cor` で、$[-1, 1]$ の値を返します。この場合、負の値は通常フィルタリングされ（ゼロ結合として解釈され）、$1$ の値は完璧な予測を意味します。[Sugihara et al. (2012)](http://science.sciencemag.org/content/early/2012/09/19/science.1227079) では、平方平均偏差を使用することも提案されており、その場合の値 $0$ は完璧な予測となります。

## 参考文献

Sugihara, George, et al. "Detecting causality in complex ecosystems." Science (2012): 1227079. [http://science.sciencemag.org/content/early/2012/09/19/science.1227079](http://science.sciencemag.org/content/early/2012/09/19/science.1227079)

Ye, Hao, et al. "Distinguishing time-delayed causal interactions using convergent cross mapping." Scientific Reports 5 (2015): 14750. [https://www.nature.com/articles/srep14750](https://www.nature.com/articles/srep14750)

Ye, H., et al. "rEDM: Applications of empirical dynamic modeling from time series." R Package Version 0.4 7 (2016). [https://cran.r-project.org/web/packages/rEDM/index.html](https://cran.r-project.org/web/packages/rEDM/index.html)
