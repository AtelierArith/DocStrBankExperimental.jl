```
branching_table(problem::AbstractProblem, table_solver::AbstractTableSolver, variables::Vector{Int})
```

指定されたテーブルソルバーを使用して、与えられた問題のブランチングテーブルを取得します。

### 引数

  * `problem`: 問題のインスタンス。
  * `table_solver`: [`AbstractTableSolver`](@ref) のサブタイプであるテーブルソルバー。
  * `variables`: ブランチングテーブルに考慮される変数のインデックスのベクター。

### 戻り値

[`BranchingTable`](@ref) オブジェクトであるブランチングテーブル。
