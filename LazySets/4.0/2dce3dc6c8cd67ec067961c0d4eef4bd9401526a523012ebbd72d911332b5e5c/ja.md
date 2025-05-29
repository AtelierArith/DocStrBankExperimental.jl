```
Projection(X::LazySet{N}, variables::AbstractVector{Int}) where {N}
```

セットの遅延射影を返します。

### 入力

  * `X`         – セット
  * `variables` – 興味のある変数

### 出力

与えられた変数 `variables` に沿った `X` の射影に対応する遅延 `LinearMap`。

### 例

三次元の立方体を最初の二つの座標に射影する：

```jldoctest Projection
julia> B = BallInf([1.0, 2, 3], 1.0)
BallInf{Float64, Vector{Float64}}([1.0, 2.0, 3.0], 1.0)

julia> Bproj = Projection(B, [1, 2])
LinearMap{Float64, BallInf{Float64, Vector{Float64}}, Float64, SparseArrays.SparseMatrixCSC{Float64, Int64}}(sparse([1, 2], [1, 2], [1.0, 1.0], 2, 3), BallInf{Float64, Vector{Float64}}([1.0, 2.0, 3.0], 1.0))

julia> isequivalent(Bproj, BallInf([1.0, 2], 1.0))
true
```
