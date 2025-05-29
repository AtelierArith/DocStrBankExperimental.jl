```
conditional_entropy(X::Matrix{<:Real}, Y::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

データセット X の条件付きエントロピーを、条件付けデータセット Y に対して H(X | Y) = H(X, Y) - H(Y) として計算します。ここで：

  * H(X, Y): X と Y の結合エントロピー。
  * H(Y): 条件付けデータセット Y のエントロピー。

# 引数

  * `X::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が主データセットの次元を表す行列。
  * `Y::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が条件付けデータセットの次元を表す行列。
  * `method::String = "inv"` (オプション): エントロピー計算に使用する方法。選択肢は：

      * `"knn"`: k-最近傍に基づくエントロピー推定。
      * `"histogram"`: ヒストグラムに基づくエントロピー推定。
      * `"inv"`: 不変エントロピー推定（デフォルト）。
  * `nbins::Int = 10` (オプション): ヒストグラム法のためのビンの数。他の方法では無視されます。デフォルトは 10。
  * `k::Int = 3` (オプション): k-NN または不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは 3。
  * `base::Real = e` (オプション): エントロピー計算のための対数の底。デフォルトは自然対数（`e`）。
  * `verbose::Bool = false` (オプション): `true` の場合、データセットと計算プロセスに関する追加情報を印刷します。デフォルトは `false`。
  * `degenerate::Bool = false` (オプション): `true` の場合、k-NN または不変法の距離にノイズを追加して退化ケースに対処します。ヒストグラム法では無視されます。デフォルトは `false`。
  * `dim::Int = 1` (オプション): データが行（`dim = 1`）または列（`dim = 2`）に整理されているかを示します。デフォルトは 1（行にデータ）。

# 戻り値

  * `Real`: 計算された条件付きエントロピー H(X | Y)。

# 挙動

  * 指定された `method` に応じて、適切なエントロピー推定関数（`entropy_knn`、`entropy_hist`、`entropy_inv`）が呼び出されます。

# 例

x = rand(1, 100)  # 1D で 100 ポイント y = rand(1, 100)  # 1D で 100 ポイント

# k-NN 法を使用

conditional*ent = conditional*entropy(x, y, method="knn", k=5, verbose=true)

# ヒストグラム法を使用

conditional*ent = conditional*entropy(x, y, method="histogram", nbins=10)

# 不変法を使用

conditional*ent = conditional*entropy(x, y, method="inv", k=3) ```
