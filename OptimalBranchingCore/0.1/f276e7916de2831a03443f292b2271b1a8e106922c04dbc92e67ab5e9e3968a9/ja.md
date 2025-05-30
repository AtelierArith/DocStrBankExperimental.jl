```
test_rule(table::BranchingTable, predicted::DNF, problem::AbstractProblem, m::AbstractMeasure, variables::Vector)
```

ルールの有効性と複雑さをテストします。

### 引数

  * `table::BranchingTable`: 分岐テーブル。
  * `predicted::DNF`: DNFの論理式。
  * `problem::AbstractProblem`: 問題。
  * `m::AbstractMeasure`: 測定。
  * `variables::Vector`: 変数。

### 戻り値

  * `is_valid::Bool`: ルールが有効かどうか。
  * `gamma::Float64`: ルールの複雑さ。
