```
prob = discretize(pde_system::PDESystem, discretization::PhysicsInformedNN)
```

これは、ModelingToolkitで定義された`PDESystem`の記号的な説明を変換し、PDEの解が解となる`OptimizationProblem`を[Optimization.jl](https://docs.sciml.ai/Optimization/stable/)のために生成します。
