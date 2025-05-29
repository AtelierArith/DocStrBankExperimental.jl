```
PseudoInverse(; alg::SciMLLinearSolveAlgorithm = KrylovJL_GMRES())
```

[`spectrum`](@ref) を解くソルバーで、`alg`として与えられた [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/) のアルゴリズムを使用して、リウビリアン [`SuperOperator`](@ref) の逆を見つけます。
