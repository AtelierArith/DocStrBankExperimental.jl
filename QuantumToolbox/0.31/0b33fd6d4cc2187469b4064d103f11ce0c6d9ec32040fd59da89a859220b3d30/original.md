```
PseudoInverse(; alg::SciMLLinearSolveAlgorithm = KrylovJL_GMRES())
```

A solver which solves [`spectrum`](@ref) by finding the inverse of Liouvillian [`SuperOperator`](@ref) using the `alg`orithms given in [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/).
