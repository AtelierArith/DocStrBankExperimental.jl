`dot_product(L,R;to_prob = true)`

二つの埋め込み間のドット積を計算し、相互作用確率の行列を返します。

左側と右側の埋め込みは同じ次元でなければなりません（例：`size(L)[2] == size(R)[2]`）が、ノードの数は異なっていても構いません（例：二部ネットワークの場合）。

# 引数

  * `L`: 左側の埋め込み
  * `R`: 右側の埋め込み
  * `to_prob`: （オプション）結果を区間 [0,1] に制限するかどうか

# 例

```julia
julia> # まず2ブロックの行列を構築します：
julia> block_matrix = reshape([ones(5,5) zeros(5,5); zeros(5,5) ones(5,5)],10,10)
julia> # そしてそれを分解します：
julia> L,R = svd_embedding(block_matrix,2) # または、自動的に L,R = svd_embedding(block_matrix)
julia> dot_product(L,R) ≈ block_matrix
```
