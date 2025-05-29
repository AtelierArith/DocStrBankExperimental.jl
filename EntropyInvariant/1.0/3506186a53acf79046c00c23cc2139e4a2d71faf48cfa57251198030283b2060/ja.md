```
redundancy(mat_1::Matrix{<:Real}, mat_2::Matrix{<:Real}, mat_3::Matrix{<:Real}; method::String = "inv", nbins::Int = 10, k::Int = 3, base::Real = e, verbose::Bool = false, degenerate::Bool = false, dim::Int = 1) -> Real
```

2つのデータセットXとYが、3つ目のデータセットZに関して共有する情報の冗長性を、I(X; Z)とI(Y; Z)の間の相互情報量を使用して計算します: R(X, Y; Z) = min(I(X; Z), I(Y; Z))

# 引数

  * `X::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が最初のデータセットXの次元を表す行列。
  * `Y::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が2番目のデータセットYの次元を表す行列。
  * `Z::Vector or Matrix{<:Real}`: 各列がデータポイントを表し、各行が3番目のデータセットZの次元を表す行列。
  * `method::String = "inv"` (オプション): 相互情報量計算に使用する方法。オプションは次の通りです:

      * `"knn"`: k-最近傍に基づく相互情報量推定。
      * `"histogram"`: ヒストグラムに基づく相互情報量推定。
      * `"inv"`: 不変相互情報量推定（デフォルト）。
  * `nbins::Int = 10` (オプション): ヒストグラム法のためのビンの数。他の方法では無視されます。デフォルトは10。
  * `k::Int = 3` (オプション): k-NNまたは不変法のための近傍の数。ヒストグラム法では無視されます。デフォルトは3。
  * `base::Real = e` (オプション): 相互情報量計算のための対数の底。デフォルトは自然対数（`e`）。
  * `verbose::Bool = false` (オプション): `true`の場合、データセットと計算プロセスに関する追加情報を印刷します。デフォルトは`false`。
  * `degenerate::Bool = false` (オプション): `true`の場合、k-NNまたは不変法の距離にノイズを追加して退化ケースを処理します。ヒストグラム法では無視されます。デフォルトは`false`。
  * `dim::Int = 1` (オプション): データが行（`dim = 1`）または列（`dim = 2`）に整理されているかを示します。デフォルトは1（行にデータ）。

# 戻り値

  * `Real`: 計算された冗長性で、XとZ、YとZの間の相互情報量の最小値として定義されます:

# 挙動

  * 指定された`method`に応じて、適切な相互情報量推定関数（`mutual_information`）が呼び出されます。

# 例

x = rand(1, 100)  # 1Dの100ポイント y = rand(1, 100)  # 1Dの100ポイント z = rand(1, 100)  # 1Dの100ポイント

# k-NN法を使用

redund = redundancy(x, y, z, method="knn", k=5, verbose=true)

# ヒストグラム法を使用

redund = redundancy(x, y, z, method="histogram", nbins=10)

# 不変法を使用

redund = redundancy(x, y, z, method="inv", k=3) ```
