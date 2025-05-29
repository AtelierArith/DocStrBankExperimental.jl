```
mutual_information(X::Matrix{<:Real}, Y::Union{Matrix{<:Real}, Nothing} = nothing; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1, optimize::Bool = false) -> Real
```

2つのデータセット間の相互情報量を計算します。I(X; Y) = H(X) + H(Y) - H(X, Y) ここで：

  * H(X): 最初のデータセットXのエントロピー。
  * H(Y): 2番目のデータセットYのエントロピー。
  * H(X, Y): XとYの結合エントロピー。

# 引数

  * X::Vector または Matrix{<:Real}`: 各列がデータポイントを表し、各行が最初のデータセットの次元を表す行列。
  * Y::Vector または Matrix{<:Real}`: 各列がデータポイントを表し、各行が2番目のデータセットの次元を表す行列。
  * `method::String = "inv"` (オプション): エントロピー計算に使用する方法。オプションは次の通りです：

      * `"knn"`: k-最近傍に基づくエントロピー推定。
      * `"histogram"`: ヒストグラムに基づくエントロピー推定。
      * `"inv"`: 不変エントロピー推定（デフォルト）。
  * `nbins::Int = 10` (オプション): ヒストグラム法のためのビンの数。他の方法では無視されます。デフォルトは10。
  * `k::Int = 3` (オプション): k-NNまたは不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは3。
  * `base::Real = e` (オプション): エントロピー計算のための対数の基数。デフォルトは自然対数（`e`）。
  * `verbose::Bool = false` (オプション): `true`の場合、データセットと計算プロセスに関する追加情報を印刷します。デフォルトは`false`。
  * `degenerate::Bool = false` (オプション): `true`の場合、k-NNまたは不変法の距離にノイズを追加して退化ケースを処理します。ヒストグラム法では無視されます。デフォルトは`false`。
  * `dim::Int = 1` (オプション): データが行（`dim = 1`）または列（`dim = 2`）に整理されているかを示します。デフォルトは1（行にデータ）。
  * `optimize::Bool = false` (オプション): `true`の場合、Xの不変二次元相互情報量をより速く計算します。デフォルトは`false`。Yは何もないべきです。

# 戻り値

  * `Real`: データセットXとY間の計算された相互情報量I(X; Y)。

# 挙動

  * 指定された`method`に応じて、適切なエントロピー推定関数（`entropy_knn`、`entropy_hist`、`entropy_inv`）が呼び出されます。

# 例

x = rand(1, 100)  # 1Dの100ポイント y = rand(1, 100)  # 1Dの100ポイント

# ヒストグラムkNN法を使用

mi = mutual_information(x, y, method="knn", k=5, verbose=true)

# ヒストグラム法を使用

mi = mutual_information(x, y, method="histogram", nbins=10)

# 不変法を使用

mi = mutual_information(x, y, method="inv", k=3) ```
