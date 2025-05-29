```julia
struct JumpInputs{S<:ModelingToolkit.JumpSystem, T<:SciMLBase.AbstractODEProblem}
```

与えられた `ReactionSystem` からの JumpProblem の入力。

# フィールド

  * `sys`: 問題を定義するための `JumpSystem`
  * `prob`: JumpProblem が定義されるべき問題、例えば DiscreteProblem
