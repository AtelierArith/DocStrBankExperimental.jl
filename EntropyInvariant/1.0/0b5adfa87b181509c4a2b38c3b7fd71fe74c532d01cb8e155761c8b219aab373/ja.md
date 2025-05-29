```
conditional_mutual_information(X::Matrix{<:Real}, Y::Union{Matrix{<:Real}, Nothing} = nothing, Z::Union{Matrix{<:Real}, Nothing} = nothing; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1, optimize::Bool = false) -> Real
```

条件付き相互情報量 (CMI) を、第三の条件付けデータセットを考慮して計算します。I(X; Y | Z) = H(X, Z) + H(Y, Z) - H(X, Y, Z) - H(Z) のように、ここで:

  * H(Z): 条件付けデータセット Z のエントロピー。
  * H(X, Z): X と Z の結合エントロピー。
  * H(Y, Z): Y と Z の結合エントロピー。
  * H(X, Y, Z): X, Y と Z の結合エントロピー。

# 引数

  * X::Vector または Matrix{<:Real}`: 各列がデータポイントを表し、各行が最初のデータセットの次元を表す行列。
  * Y::Vector または Matrix{<:Real}`: 各列がデータポイントを表し、各行が第二のデータセットの次元を表す行列。
  * Z::Vector または Matrix{<:Real}`: 各列がデータポイントを表し、各行が条件付けデータセットの次元を表す行列。
  * `method::String = "inv"` (オプション): エントロピー計算に使用する方法。選択肢は:

      * `"knn"`: k-最近傍に基づくエントロピー推定。
      * `"histogram"`: ヒストグラムに基づくエントロピー推定。
      * `"inv"`: 不変エントロピー推定 (デフォルト)。
  * `nbins::Int = 10` (オプション): ヒストグラム法のためのビンの数。他の方法では無視されます。デフォルトは10。
  * `k::Int = 3` (オプション): k-NN または不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは3。
  * `base::Real = e` (オプション): エントロピー計算のための対数の底。デフォルトは自然対数 (`e`)。
  * `verbose::Bool = false` (オプション): `true` の場合、データセットと計算プロセスに関する追加情報を印刷します。デフォルトは `false`。
  * `degenerate::Bool = false` (オプション): `true` の場合、k-NN または不変法の距離にノイズを追加して退化ケースを処理します。ヒストグラム法では無視されます。デフォルトは `false`。
  * `dim::Int = 1` (オプション): データが行 (`dim = 1`) または列 (`dim = 2`) に整理されているかを示します。デフォルトは1（行にデータ）。
  * `optimize::Bool = false` (オプション): `true` の場合、X と Z の不変二次元条件付き相互情報量をより速く計算します。デフォルトは `false`。Y は何も指定しない必要があります。

# 戻り値

  * `Real`: 計算された条件付き相互情報量 I(X; Y | Z)

# 挙動

  * 指定された `method` に応じて、適切なエントロピー推定関数 (`entropy_knn`, `entropy_hist`, `entropy_inv`) が呼び出されます。

# 例

x = rand(1, 100)  # 1D の 100 ポイント y = rand(1, 100)  # 1D の 100 ポイント z = rand(1, 100)  # 1D の 100 ポイント

# k-NN 法を使用

cmi = conditional*mutual*information(x, y, z, method="knn", k=5, verbose=true)

# ヒストグラム法を使用

cmi = conditional*mutual*information(x, y, z, method="histogram", nbins=10)

# 不変法を使用

cmi = conditional*mutual*information(x, y, z, method="inv", k=3) ```
