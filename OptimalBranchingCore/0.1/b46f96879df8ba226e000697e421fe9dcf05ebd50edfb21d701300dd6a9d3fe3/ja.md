```
optimal_branching_rule(table::BranchingTable, variables::Vector, problem::AbstractProblem, measure::AbstractMeasure, solver::AbstractSetCoverSolver)::OptimalBranchingResult
```

与えられた分岐テーブルから最適な分岐ルールを生成します。

### 引数

  * `table`: 候補句を含む [`BranchingTable`](@ref) インスタンス。
  * `variables`: 分岐を行うための変数のベクター。
  * `problem`: 解決されている問題インスタンス。
  * `measure`: 分岐における問題サイズの削減を評価するために使用される測定。
  * `solver`: 重み付き最小集合被覆問題に使用されるソルバーで、[`LPSolver`](@ref) または [`IPSolver`](@ref) のいずれかです。

### 戻り値

最適な分岐ルールを表す [`OptimalBranchingResult`](@ref) オブジェクト。
