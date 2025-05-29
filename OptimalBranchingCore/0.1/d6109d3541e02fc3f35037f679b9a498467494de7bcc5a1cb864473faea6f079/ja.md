```
BranchingStrategy
BranchingStrategy(; kwargs...)
```

ソルバーの設定を表す構造体で、リデューサーとブランチング戦略を含みます。

### フィールド

  * `table_solver::AbstractTableSolver`: 関連するビット列を解決し、ブランチングテーブルを生成するソルバー。
  * `set_cover_solver::AbstractSetCoverSolver = IPSolver()`: セットカバー問題を解決するソルバー。
  * `selector::AbstractSelector`: 次のブランチ変数または決定を選択するためのセレクター。
  * `m::AbstractMeasure`: ブランチング戦略のパフォーマンスを評価するための測定。
