```
interaction_information(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}, mat_3::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3,base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

三つのデータセット間の相互情報量 (II) を計算します。II(X; Y; Z) = H(X) + H(Y) + H(Z) - H(X, Y) - H(X, Z) - H(Y, Z) + H(X, Y, Z) であり、以下のように定義されます：

  * H(X), H(Y), H(Z): 各データセットのエントロピー。
  * H(X, Y), H(X, Z), H(Y, Z): ペアワイズの結合エントロピー。
  * H(X, Y, Z): 三つのデータセットの結合エントロピー。

# 引数

  * `X::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が最初のデータセットの次元を表す行列。
  * `Y::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が二番目のデータセットの次元を表す行列。
  * `Z::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が三番目のデータセットの次元を表す行列。
  * `method::String = "inv"` (オプション): エントロピー計算に使用する方法。選択肢は：

      * `"knn"`: k-最近傍に基づくエントロピー推定。
      * `"histogram"`: ヒストグラムに基づくエントロピー推定。
      * `"inv"`: 不変エントロピー推定（デフォルト）。
  * `nbins::Int = 10` (オプション): ヒストグラム法のためのビンの数。他の方法では無視されます。デフォルトは10。
  * `k::Int = 3` (オプション): k-NNまたは不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは3。
  * `base::Real = e` (オプション): エントロピー計算のための対数の底。デフォルトは自然対数（`e`）。
  * `verbose::Bool = false` (オプション): `true`の場合、データセットと計算プロセスに関する追加情報を表示します。デフォルトは`false`。
  * `degenerate::Bool = false` (オプション): `true`の場合、k-NNまたは不変法の距離にノイズを追加して退化ケースを処理します。ヒストグラム法では無視されます。デフォルトは`false`。
  * `dim::Int = 1` (オプション): データが行（`dim = 1`）または列（`dim = 2`）で整理されているかを示します。デフォルトは1（行にデータ）。

# 戻り値

  * `Real`: データセット X, Y, Z 間の計算された相互情報量 II(X; Y; Z)。

# 挙動

  * 指定された `method` に応じて、適切なエントロピー推定関数（`entropy_knn`、`entropy_hist`、`entropy_inv`）が呼び出されます。

# 例

x = rand(1, 100)  # 1Dの100ポイント y = rand(1, 100)  # 1Dの100ポイント z = rand(1, 100)  # 1Dの100ポイント

# k-NN法を使用

ii = interaction_information(x, y, z, method="knn", k=5, verbose=true)

# ヒストグラム法を使用

ii = interaction_information(x, y, z, method="histogram", nbins=10)

# 不変法を使用

ii = interaction_information(x, y, z, method="inv", k=3) ```
