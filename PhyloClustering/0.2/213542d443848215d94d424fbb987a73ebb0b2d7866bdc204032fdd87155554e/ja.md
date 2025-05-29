```
gmm_label(tree::AbstractMatrix{<:Real}, n::Int64; method::Symbol=:kmeans, kind::Symbol=:diag)
```

系統樹のグループに対するガウス混合モデルから予測ラベルを取得します。

# 引数

  * `tree`: B * N の木行列（木行列の各列は二分割形式の B 次元の木です）。
  * `n`: クラスターの数。
  * `method`（デフォルトは `:kmeans`）: n 個の初期中心を見つけるための初期化方法:      * `:kmeans`: [Clustering.jl](https://github.com/JuliaStats/Clustering.jl) から K-means クラスタリングを使用して `n` 個の中心で初期化します。      * `:split`: `tree` で単一のガウスを初期化し、その後ガウスを分割し、EM アルゴリズムを使用して再訓練し、`n` 個のガウスが得られるまで続けます。
  * `kind`（デフォルトは `:diag`）: 共分散の種類、`:diag` または `:full`。

# 出力

`Tuple{Vector{Int64}, Vector{Int64}}` で、最初の `Vector` には後方確率に基づく各木の予測ラベルが含まれ、第二の `Vector` には対数尤度に基づく各木の予測ラベルが含まれます。
