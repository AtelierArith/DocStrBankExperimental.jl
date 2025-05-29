```
pointwise_log_likelihoods(
    ll_fun::Function, samples::AbstractArray{<:Real,3}, data;
    splat::Bool=true[, chain_index::Vector{<:Integer}]
)
```

点ごとの対数尤度を計算します。

# 引数

  * `ll_fun::Function`: 単一のデータポイントを受け取り、そのポイントの対数尤度を返す関数。この関数は `f(θ[1], ..., θ[n], data)` の形式である必要があり、ここで `θ` はパラメータベクトルです。`splat` キーワード引数も参照してください。
  * `samples::AbstractArray`: MCMCサンプルの三次元配列。ここで、最初の次元はMCMCアルゴリズムのステップを示し、2番目の次元はパラメータを示し、3番目はチェーンを示します。
  * `data`: モデルのパラメータを推定するために使用されるデータポイントの配列。
  * `splat`: `true`（デフォルト）の場合、`f` は `n` 個の異なるパラメータの関数である必要があります。そうでない場合、`f` は単一のパラメータベクトルの関数であると見なされます。
  * `chain_index::Vector{Int}`: 各ステップがどのチェーンに属するかを指定する整数のオプションベクトル。たとえば、`chain_index[step]` は `log_likelihood[:, step]` が第二のチェーンに属する場合、`2` を返す必要があります。

# 戻り値

  * `Array`: 点ごとの対数尤度の三次元配列。
