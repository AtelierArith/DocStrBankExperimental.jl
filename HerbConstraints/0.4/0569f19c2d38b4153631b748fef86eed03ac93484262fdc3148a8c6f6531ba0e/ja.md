```
mutable struct SolverState
```

[`GenericSolver`](@ref)によって解決される状態。状態は以下を含みます：

  * `tree`: 部分的なAST
  * `active_constraints`: この木に適用されるローカル制約。これらの制約は、木が変更されるたびに強制されます。
  * `isfeasible`: この状態がまだ実現可能かどうかを示すフラグ。伝播者が不整合を検出すると、このフィールドはfalseに設定されます。不実現可能な状態では木の操作やさらなる伝播は許可されません。
