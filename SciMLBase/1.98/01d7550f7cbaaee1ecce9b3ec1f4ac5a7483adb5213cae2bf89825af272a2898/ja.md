```julia
abstract type AbstractDEProblem <: SciMLBase.AbstractSciMLProblem
```

DifferentialEquations.jl のすべての問題のベースタイプ。`AbstractDEProblem` の具体的なサブタイプは、対応するタイプの微分方程式を完全に定義するために必要な情報を含んでいます。
