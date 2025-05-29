```julia
abstract type PolicySolution <: SymbolicPlanners.Solution
```

ポリシーソリューションのための抽象型。最小限、`PolicySolution`は特定の`state`で取られる（潜在的にランダムな）アクションを定義する`get_action(sol, state::State)`メソッドを実装する必要があります。
