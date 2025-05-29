```
coloring(
    S::AbstractMatrix,
    problem::ColoringProblem,
    algo::GreedyColoringAlgorithm;
    [decompression_eltype=Float64, symmetric_pattern=false]
)
```

行列 `S` に対して [`ColoringProblem`](@ref) を解決し、[`GreedyColoringAlgorithm`](@ref) を使用して [`AbstractColoringResult`](@ref) を返します。

結果は、同じスパースパターンを持つ行列 `A` を [`compress`](@ref) および [`decompress`](@ref) するために使用できます。もし `eltype(A) == decompression_eltype` であれば、デコンプレッションがより速くなる可能性があります。

`:nonsymmetric` 問題の場合（その場合のみ）、`symmetric_pattern=true` を設定すると、非ゼロのパターンが対称であることを示します。この条件は実際の値の対称性よりも弱いため、いくつかのヤコビ行列に対して発生する可能性があります。これを指定することで、二部グラフの構築が速くなります。

# 例

```jldoctest
julia> using SparseMatrixColorings, SparseArrays

julia> S = sparse([
           0 0 1 1 0 1
           1 0 0 0 1 0
           0 1 0 0 1 0
           0 1 1 0 0 0
       ]);

julia> problem = ColoringProblem(; structure=:nonsymmetric, partition=:column);

julia> algo = GreedyColoringAlgorithm(; decompression=:direct);

julia> result = coloring(S, problem, algo);

julia> column_colors(result)
6-element Vector{Int64}:
 1
 1
 2
 1
 2
 3

julia> collect.(column_groups(result))
3-element Vector{Vector{Int64}}:
 [1, 2, 4]
 [3, 5]
 [6]
```

# 参照

  * [`ColoringProblem`](@ref)
  * [`GreedyColoringAlgorithm`](@ref)
  * [`AbstractColoringResult`](@ref)
  * [`compress`](@ref)
  * [`decompress`](@ref)

```
