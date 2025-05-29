```
decompress_single_color!(
    A::AbstractMatrix, b::AbstractVector, c::Integer,
    result::AbstractColoringResult, [uplo=:F]
)
```

色 `c` に対応するベクトル `b` を、スパースパターン `A` の `:direct` 彩色 `result` に基づいて、インプレースで `A` にデコンプレッションします（`:substitution` 彩色では機能しません）。

  * `result` が `:column` パーティションを持つ `:nonsymmetric` 構造から来る場合、これは色 `c` を共有する `A` の列を更新します（その合計が `b` を構成します）。
  * `result` が `:row` パーティションを持つ `:nonsymmetric` 構造から来る場合、これは色 `c` を共有する `A` の行を更新します（その合計が `b` を構成します）。
  * `result` が `:column` パーティションを持つ `:symmetric` 構造から来る場合、これは色 `c` から推測される `A` の係数を更新します。

!!! warning
    この関数は `A` の一部の係数のみを更新し、残りをゼロにリセットすることはありません。


`symmetric` 彩色結果（およびそれにのみ）に対して、オプションの位置引数 `uplo in (:U, :L, :F)` を渡すことで、更新すべき行列 `A` の部分を指定できます：上三角、下三角、または全行列。`A` が `SparseMatrixCSC` の場合、`uplo` 引数を使用するには、関連する三角形のみを格納するターゲット行列が必要です。

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

julia> A2 = similar(A); A2 .= 0;

julia> decompress_single_color!(A2, B[:, 2], 2, result)
4×6 SparseMatrixCSC{Int64, Int64} with 9 stored entries:
 ⋅  ⋅  4  0  ⋅  0
 0  ⋅  ⋅  ⋅  7  ⋅
 ⋅  0  ⋅  ⋅  8  ⋅
 ⋅  0  5  ⋅  ⋅  ⋅

julia> A2[:, [3, 5]] == A[:, [3, 5]]
true
```

# 参照

  * [`ColoringProblem`](@ref)
  * [`AbstractColoringResult`](@ref)
  * [`decompress!`](@ref)
