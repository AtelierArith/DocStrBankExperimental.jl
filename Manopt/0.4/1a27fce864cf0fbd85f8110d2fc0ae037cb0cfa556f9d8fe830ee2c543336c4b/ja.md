```
AbstractHessianSolverState <: AbstractGradientSolverState
```

[`AbstractManoptSolverState`](@ref) 型は、ヘッセ行列を使用するアルゴリズムを表します。これらのオプションは、現在の勾配 $\operatorname{grad}f(x)$ を格納するフィールド（`gradient`）を持つと仮定されています。
