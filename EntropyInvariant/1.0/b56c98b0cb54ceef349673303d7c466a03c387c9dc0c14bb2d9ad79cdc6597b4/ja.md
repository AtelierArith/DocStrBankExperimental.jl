```
unique(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}, mat_3::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Tuple{Real, Real}
```

データセット X と Y が、第三のデータセット Z に対して個別に貢献するユニークな情報を次のように計算します: U(X; Z) = I(X; Z) - R(X, Y; Z) U(Y; Z) = I(Y; Z) - R(X, Y; Z) ここで:

  * R(X, Y; Z) = min(I(X; Z), I(Y; Z)) は Z に関する X と Y の冗長性です。

# 引数

  * `X::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が最初のデータセット X の次元を表す行列。
  * `Y::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が第二のデータセット Y の次元を表す行列。
  * `Z::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が第三のデータセット Z の次元を表す行列。
  * `method::String = "inv"` (オプション): 相互情報量計算に使用する方法。オプションは次の通りです:

      * `"knn"`: k-最近傍に基づく相互情報量推定。
      * `"histogram"`: ヒストグラムに基づく相互情報量推定。
      * `"inv"`: 不変相互情報量推定（デフォルト）。
  * `nbins::Int = 10` (オプション): ヒストグラム法のためのビンの数。他の方法では無視されます。デフォルトは 10。
  * `k::Int = 3` (オプション): k-NN または不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは 3。
  * `base::Real = e` (オプション): 相互情報量計算のための対数の基数。デフォルトは自然対数（`e`）。
  * `verbose::Bool = false` (オプション): `true` の場合、データセットと計算プロセスに関する追加情報を印刷します。デフォルトは `false`。
  * `degenerate::Bool = false` (オプション): `true` の場合、k-NN または不変法のために距離にノイズを追加して退化ケースを処理します。ヒストグラム法では無視されます。デフォルトは `false`。
  * `dim::Int = 1` (オプション): データが行（`dim = 1`）または列（`dim = 2`）に整理されているかを示します。デフォルトは 1（行にデータ）。

# 戻り値

  * `Tuple{Real, Real}`: タプル (U(X; Z), U(Y; Z))。

# 挙動

  * 指定された `method` に応じて、適切な相互情報量推定関数（`mutual_information`）が呼び出されます。

# 例

x = rand(1, 100)  # 1D の 100 ポイント y = rand(1, 100)  # 1D の 100 ポイント z = rand(1, 100)  # 1D の 100 ポイント

# k-NN 法を使用

unique*x, unique*y = unique(x, y, z, method="knn", k=5, verbose=true)

# ヒストグラム法を使用

unique*x, unique*y = unique(x, y, z, method="histogram", nbins=10)

# 不変法を使用

unique*x, unique*y = unique(x, y, z, method="inv", k=3) ```
