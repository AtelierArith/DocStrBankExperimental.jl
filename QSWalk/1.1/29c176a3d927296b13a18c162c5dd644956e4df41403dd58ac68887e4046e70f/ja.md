```
local_lind(A[; epsilon])
```

行列 `A` の要素を、正確に1つの非ゼロ要素を持つ疎行列のコレクションに分割します。非ゼロ要素の絶対値が `epsilon` より小さくない場合に行列が作成されます。`epsilon` は非負である必要があります。指定されていない場合、`epsilon` は `eps()` にデフォルト設定されます。

# 例

```jldoctest; setup = :(using QSWalk)
julia> A = [1. 2.; 3. 4.]
2×2 Array{Float64,2}:
 1.0  2.0
 3.0  4.0

julia> local_lind(A)
4-element Array{SparseArrays.SparseMatrixCSC{Float64,Ti} where Ti<:Integer,1}:

  [1, 1]  =  1.0

  [1, 2]  =  2.0

  [2, 1]  =  3.0

  [2, 2]  =  4.0

julia> local_lind(A, epsilon = 1.5)
3-element Array{SparseArrays.SparseMatrixCSC{Float64,Ti} where Ti<:Integer,1}:

  [1, 2]  =  2.0

  [2, 1]  =  3.0

  [2, 2]  =  4.0

```
