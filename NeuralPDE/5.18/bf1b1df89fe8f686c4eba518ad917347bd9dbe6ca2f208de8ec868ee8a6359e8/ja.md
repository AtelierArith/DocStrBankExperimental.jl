```
prob = symbolic_discretize(pde_system::PDESystem, discretization::AbstractPINN)
```

`symbolic_discretize` は、内部を検査するための `discretize` の低レベルインターフェースです。これは、ModelingToolkitで定義された `PDESystem` の象徴的な記述を `PINNRepresentation` に変換し、これにより、[Optimization.jl](https://docs.sciml.ai/Optimization/stable) のための `OptimizationProblem` を構築するために必要な要素や、HMCベースの事後サンプリングアルゴリズム用の尤度関数 [AdvancedHMC.jl](https://turinglang.org/AdvancedHMC.jl/stable/) を保持します。これらは後に最適化され、PDEの解または解の分布を提供します。

詳細については、`discretize` と `PINNRepresentation` を参照してください。
