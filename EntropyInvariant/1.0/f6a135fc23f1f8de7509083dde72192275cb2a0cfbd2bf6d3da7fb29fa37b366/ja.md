```
normalized_mutual_information(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

2つのデータセット間の正規化相互情報量 (NMI) を計算します。NMI(X, Y) = max(0, H(X) + H(Y) - H(X, Y))/(H(X) + H(Y)) であり、ここで:

  * H(X): 最初のデータセット X のエントロピー。
  * H(Y): 2番目のデータセット Y のエントロピー。
  * H(X, Y): X と Y の結合エントロピー。

# 引数

  * X::Vector または Matrix{<:Real}`: 各列がデータポイントを表し、各行が最初のデータセットの次元を表す行列。
  * Y::Vector または Matrix{<:Real}`: 各列がデータポイントを表し、各行が2番目のデータセットの次元を表す行列。
  * `method::String = "inv"` (オプション): エントロピー計算に使用する方法。オプションは次の通りです:

      * `"knn"`: k-最近傍に基づくエントロピー推定。
      * `"histogram"`: ヒストグラムに基づくエントロピー推定。
      * `"inv"`: 不変エントロピー推定 (デフォルト)。
  * `nbins::Int = 10` (オプション): ヒストグラム法のビンの数。他の方法では無視されます。デフォルトは10。
  * `k::Int = 3` (オプション): k-NN または不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは3。
  * `base::Real = e` (オプション): エントロピー計算の対数の基数。デフォルトは自然対数 (`e`)。
  * `verbose::Bool = false` (オプション): `true` の場合、データセットと計算プロセスに関する追加情報を印刷します。デフォルトは `false`。
  * `degenerate::Bool = false` (オプション): `true` の場合、k-NN または不変法の距離にノイズを追加して退化ケースを処理します。ヒストグラム法では無視されます。デフォルトは `false`。
  * `dim::Int = 1` (オプション): データが行 (`dim = 1`) または列 (`dim = 2`) に整理されているかを示します。デフォルトは1 (行にデータ)。

# 戻り値

  * `Real`: X と Y の間の正規化相互情報量 NMI(X, Y)。

      * 0 < NMI < 1 であり、0 は共有情報がないことを示し、1 は完全な相互情報を示します。

# 挙動

  * 指定された `method` に応じて、適切なエントロピー推定関数 (`entropy_knn`, `entropy_hist`, `entropy_inv`) が呼び出されます。

# 例

x = rand(1, 100)  # 1D の 100 ポイント y = rand(1, 100)  # 1D の 100 ポイント

# k-NN 法を使用

nmi = normalized*mutual*information(x, y, method="knn", k=5, verbose=true)

# ヒストグラム法を使用

nmi = normalized*mutual*information(x, y, method="histogram", nbins=10)

# 不変法を使用

nmi = normalized*mutual*information(x, y, method="inv", k=3) ```
