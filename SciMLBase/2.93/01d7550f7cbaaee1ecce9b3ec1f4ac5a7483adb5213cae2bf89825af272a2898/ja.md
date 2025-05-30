```julia
abstract type AbstractDEProblem <: SciMLBase.AbstractSciMLProblem
```

DifferentialEquations.jlのすべての問題のための基本型。`AbstractDEProblem`の具体的なサブタイプは、対応するタイプの微分方程式を完全に定義するために必要な情報を含んでいます。
