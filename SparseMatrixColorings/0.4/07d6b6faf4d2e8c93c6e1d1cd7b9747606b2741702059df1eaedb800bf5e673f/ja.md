```
decompress(B::AbstractMatrix, result::AbstractColoringResult{_,:column/:row})
decompress(Br::AbstractMatrix, Bc::AbstractMatrix, result::AbstractColoringResult{_,:bidirectional})
```

行列 `B`（またはタプル `(Br,Bc)`）を新しい行列 `A` にデコンプレッションし、`A` のスパースパターンの色付け `result` を与えます。インプレースの代替手段は [`decompress!`](@ref) です。

圧縮とは、同じ色を持つ `A` の列または行を合計することを意味します。これは [`compress`](@ref) を呼び出すことで行われます。

# 例

```jldoctest
julia> using SparseMatrixColorings, SparseArrays

julia> A = sparse([
           0 0 4 6 0 9
           1 0 0 0 7 0
           0 2 0 0 8 0
           0 3 5 0 0 0
       ]);

julia> result = coloring(A, ColoringProblem(), GreedyColoringAlgorithm());

julia> collect.(column_groups(result))
3-element Vector{Vector{Int64}}:
 [1, 2, 4]
 [3, 5]
 [6]

julia> B = compress(A, result)
4×3 Matrix{Int64}:
 6  4  9
 1  7  0
 2  8  0
 3  5  0

julia> decompress(B, result)
4×6 SparseMatrixCSC{Int64, Int64} with 9 stored entries:
 ⋅  ⋅  4  6  ⋅  9
 1  ⋅  ⋅  ⋅  7  ⋅
 ⋅  2  ⋅  ⋅  8  ⋅
 ⋅  3  5  ⋅  ⋅  ⋅

julia> decompress(B, result) == A
true
```

# 参照

  * [`ColoringProblem`](@ref)
  * [`AbstractColoringResult`](@ref)
