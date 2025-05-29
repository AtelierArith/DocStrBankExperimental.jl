```
compress(A, result::AbstractColoringResult)
```

与えられた色付け `result` に基づいて `A` を圧縮します。

  * `result` が `:column`（または `:row`）パーティションから来ている場合、出力は列（または行）で圧縮された単一の行列 `B` です。
  * `result` が `:bidirectional` パーティションから来ている場合、出力は行で圧縮された `Br` と列で圧縮された `Bc` の行列のタプル `(Br, Bc)` です。

圧縮とは、同じ色を持つ `A` の列または行を合計することを意味します。これは、[`decompress`](@ref) または [`decompress!`](@ref) を呼び出すことで元に戻されます。

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
```

# 参照

  * [`ColoringProblem`](@ref)
  * [`AbstractColoringResult`](@ref)
