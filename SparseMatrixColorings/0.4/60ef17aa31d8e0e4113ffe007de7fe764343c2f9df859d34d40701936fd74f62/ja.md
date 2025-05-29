```
decompress!(
    A::AbstractMatrix, B::AbstractMatrix,
    result::AbstractColoringResult{_,:column/:row}, [uplo=:F]
)

decompress!(
    A::AbstractMatrix, Br::AbstractMatrix, Bc::AbstractMatrix
    result::AbstractColoringResult{_,:bidirectional}
)
```

`B`（またはタプル `(Br,Bc)`）を、`A` のスパースパターンの色付け `result` に基づいてインプレースでデコンプレッションします。アウトオブプレースの代替手段は [`decompress`](@ref) です。

!!! note
    インプレースデコンプレッションは、`A isa SparseMatrixCSC` の場合に高速です。


圧縮とは、同じ色を持つ `A` の列または行を合計することを意味します。これは [`compress`](@ref) を呼び出すことで行われます。

`:symmetric` 色付け結果（およびそれに限る）に対して、オプションの位置引数 `uplo in (:U, :L, :F)` を渡すことで、更新すべき行列 `A` の部分を指定できます：上三角、下三角、または全行列。`A isa SparseMatrixCSC` の場合、`uplo` 引数を使用するには、関連する三角形のみを格納するターゲット行列が必要です。

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

julia> A2 = similar(A);

julia> decompress!(A2, B, result)
4×6 SparseMatrixCSC{Int64, Int64} with 9 stored entries:
 ⋅  ⋅  4  6  ⋅  9
 1  ⋅  ⋅  ⋅  7  ⋅
 ⋅  2  ⋅  ⋅  8  ⋅
 ⋅  3  5  ⋅  ⋅  ⋅

julia> A2 == A
true
```

# 参照

  * [`ColoringProblem`](@ref)
  * [`AbstractColoringResult`](@ref)
