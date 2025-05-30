```
fit(DiffMap, data; maxoutdim=2, t=1, α=0.0, ɛ=1.0)
```

`data`にアイソメトリックマッピングモデルをフィットさせます。

# 引数

  * `data::Matrix`: 観測の$d \times n$行列。`data`の各列は

観測であり、`d`は特徴の数、`n`は観測の数です。

# キーワード引数

  * `kernel::Union{Nothing, Function}`: カーネル関数。

2つの入力ベクトル（観測）をスカラー（類似性の尺度）にマッピングします。デフォルトでは、ガウスカーネルです。`kernel`が`nothing`に設定されている場合、`data`は代わりに$n \times n$の事前計算されたグラム行列であると見なします。

  * `ɛ::Real=1.0`: ガウスカーネルの分散（スケールパラメータ）。カスタム`kernel`が渡された場合は無視されます。
  * `maxoutdim::Int=2`: 縮小された空間の次元。
  * `t::Int=1`: 遷移の数
  * `α::Real=0.0`: 正規化パラメータ

# 例

```julia
X = rand(3, 100)     # おもちゃのデータ行列、100の観測

# デフォルトのカーネル
M = fit(DiffMap, X)  # 拡散マップモデルを構築
R = transform(M)     # 次元削減を実行

# カスタムカーネル
kernel = (x, y) -> x' * y # 線形カーネル
M = fit(DiffMap, X, kernel=kernel)

# 事前計算されたグラム行列
kernel = (x, y) -> x' * y # 線形カーネル
K = ManifoldLearning.pairwise(kernel, eachcol(X), symmetric=true)
M = fit(DiffMap, K, kernel=nothing)
```
