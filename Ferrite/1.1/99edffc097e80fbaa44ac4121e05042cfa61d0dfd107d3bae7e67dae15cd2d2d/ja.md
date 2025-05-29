```
BlockSparsityPattern(block_sizes::Vector{Int})
```

与えられた `block_sizes` によって行と列のブロックサイズを持つ空の `BlockSparsityPattern` を作成します。

# 例

```julia
# ブロックサイズ 10 x 5 のブロックスパースパターンを作成
sparsity_pattern = BlockSparsityPattern([10, 5])
```

# メソッド

次のメソッドは `BlockSparsityPattern` に適用されます（詳細についてはそれぞれのドキュメントを参照してください）：

  * [`add_sparsity_entries!`](@ref): [`add_cell_entries!`](@ref)、[`add_interface_entries!`](@ref)、および [`add_constraint_entries!`](@ref) を呼び出すための便利なメソッドです。
  * [`add_cell_entries!`](@ref): セル内のDoF結合に対応するエントリを追加します。
  * [`add_interface_entries!`](@ref): セル間のインターフェース上のDoF結合に対応するエントリを追加します。
  * [`add_constraint_entries!`](@ref): 制約から生じるエントリを追加します。
  * [`allocate_matrix`](@ref allocate_matrix(::SparsityPattern)): パターンから（ブロック）行列をインスタンス化します。デフォルトの行列タイプは `BlockMatrix{Float64, Matrix{SparseMatrixCSC{Float64, Int}}}` であり、すなわち個々のブロックが `SparseMatrixCSC{Float64, Int}` 型の `BlockMatrix` です。

!!! note "パッケージ拡張"
    この機能は、パッケージ [BlockArrays.jl](https://github.com/JuliaArrays/BlockArrays.jl) がインストールされている場合（`pkg> add BlockArrays`）およびセッションでロードされている場合（`using BlockArrays`）にのみ有効です。

