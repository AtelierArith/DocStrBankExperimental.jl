```
SparsityPattern(nrows::Int, ncols::Int; nnz_per_row::Int = 8)
```

`nrows` 行と `ncols` 列を持つ空の [`SparsityPattern`](@ref) を作成します。 `nnz_per_row` は、行ごとの非ゼロエントリの数のメモリヒントとして使用されます。

`SparsityPattern` は標準の DofHandler のデフォルトのスパースパターンタイプであり、したがってこのコンストラクタではなく、[`init_sparsity_pattern`](@ref) を使用して一般的に構築されます。

# 例

```julia
# 100 x 100 行列のスパースパターンを作成し、行ごとに10エントリをヒント
sparsity_pattern = SparsityPattern(100, 100; nnz_per_row = 10)
```

# メソッド

以下のメソッドは `SparsityPattern` に適用されます（詳細についてはそれぞれのドキュメントを参照してください）：

  * [`add_sparsity_entries!`](@ref): [`add_cell_entries!`](@ref)、[`add_interface_entries!`](@ref)、および [`add_constraint_entries!`](@ref) を呼び出すための便利なメソッドです。
  * [`add_cell_entries!`](@ref): セル内の DoF カップリングに対応するエントリを追加します。
  * [`add_interface_entries!`](@ref): セル間のインターフェース上の DoF カップリングに対応するエントリを追加します。
  * [`add_constraint_entries!`](@ref): 制約から生じるエントリを追加します。
  * [`allocate_matrix`](@ref allocate_matrix(::SparsityPattern)): パターンから行列をインスタンス化します。デフォルトの行列タイプは `SparseMatrixCSC{Float64, Int}` です。

```
