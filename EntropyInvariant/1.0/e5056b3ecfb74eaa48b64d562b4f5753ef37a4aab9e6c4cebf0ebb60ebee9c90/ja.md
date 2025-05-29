```
entropy(X::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

データセットのエントロピーをいくつかの方法のいずれかを使用して計算します。

# 引数

  * `X::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が次元を表す行列。
  * `method::String = "inv"` (オプション): エントロピー計算に使用する方法。オプションは次のとおりです。

      * `"knn"`: k-最近傍法 (k-NN) に基づくエントロピー推定。
      * `"histogram"`: ヒストグラムに基づくエントロピー推定。
      * `"inv"`: 不変エントロピー推定 (デフォルト)。
  * `nbins::Int = 10` (オプション): ヒストグラム法のためのビンの数。他の方法では無視されます。デフォルトは10。
  * `k::Int = 3` (オプション): k-NNまたは不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは3。
  * `base::Real = e` (オプション): エントロピー計算のための対数の底。デフォルトは自然対数 (`e`)。
  * `verbose::Bool = false` (オプション): `true`の場合、データセットと計算プロセスに関する追加情報を印刷します。デフォルトは`false`。
  * `degenerate::Bool = false` (オプション): `true`の場合、k-NNまたは不変法の距離にノイズを追加して退化ケースを処理します。ヒストグラム法では無視されます。デフォルトは`false`。
  * `dim::Int = 1` (オプション): データが行 (`dim = 1`) または列 (`dim = 2`) に整理されているかを示します。デフォルトは1（行にデータ）。

# 戻り値

  * `Real`: データセットの計算されたエントロピー。

# 挙動

  * 関数は`method`引数に基づいてエントロピー推定方法を選択します：

    1. **k-NN法** (`method = "knn"`):

          * 最近傍距離に基づいてエントロピーを推定します。
    2. **ヒストグラム法** (`method = "histogram"`):

          * データのヒストグラムを使用してエントロピーを推定します。
    3. **不変法** (`method = "inv"`):

          * 最近傍を使用して不変スケーリング特性でエントロピーを推定します。
  * 指定された方法に基づいて適切なエントロピー関数（`entropy_knn`、`entropy_hist`、または`entropy_inv`）が呼び出されます。

# 例

# k-NN法を使用

data = rand(1, 100)  # 1次元に100ポイント println("エントロピー (k-NN): ", entropy(data, method="knn", k=5, verbose=true))

# ヒストグラム法を使用

data = rand(100)  # 1次元に100ポイント println("エントロピー (ヒストグラム): ", entropy(data, method="histogram", nbins=10) )

# 不変法を使用

println("エントロピー (不変): ", entropy(data, method="inv", k=3)) ```
