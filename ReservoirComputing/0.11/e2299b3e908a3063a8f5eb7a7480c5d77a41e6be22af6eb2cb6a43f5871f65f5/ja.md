```
rand_sparse([rng], [T], dims...;
    radius=1.0, sparsity=0.1, std=1.0, return_sparse=false)
```

ランダムなスパースリザーバ行列を作成して返します。行列のサイズは `dims` で指定され、指定された `sparsity` と `radius` に従ってスケーリングされたスペクトル半径を持ちます。

# 引数

  * `rng`: ランダム数生成器。デフォルトは WeightInitializers の `Utils.default_rng()` です。
  * `T`: リザーバ行列の要素の型。デフォルトは `Float32` です。
  * `dims`: リザーバ行列の次元。

# キーワード引数

  * `radius`: リザーバの望ましいスペクトル半径。デフォルトは 1.0 です。
  * `sparsity`: リザーバ行列のスパースレベルで、ゼロ要素の割合を制御します。デフォルトは 0.1 です。
  * `return_sparse`: `sparse` 行列を返すためのフラグ。デフォルトは `false` です。

# 例

```jldoctest
julia> res_matrix = rand_sparse(5, 5; sparsity=0.5)
5×5 Matrix{Float32}:
 0.0        0.0        0.0        0.0      0.0
 0.0        0.794565   0.0        0.26164  0.0
 0.0        0.0       -0.931294   0.0      0.553706
 0.723235  -0.524727   0.0        0.0      0.0
 1.23723    0.0        0.181824  -1.5478   0.465328
```
