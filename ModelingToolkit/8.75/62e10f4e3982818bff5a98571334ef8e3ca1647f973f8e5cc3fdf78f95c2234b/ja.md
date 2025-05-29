```julia
DiffEqBase.DiscreteProblemExpr(sys::JumpSystem, u0map, tspan,
                               parammap = DiffEqBase.NullParameters; kwargs...)
```

ジャンプシステムのための空の DiscreteProblem を生成し、解決する `prob.prob` として利用します。これは、システムに関連する ODE や SDE がない場合に使用されます。

[`JumpSystem`](@ref) 定義からの例を続けます：

```julia
using DiffEqBase, JumpProcesses
u₀map = [S => 999, I => 1, R => 0]
parammap = [β => 0.1 / 1000, γ => 0.01]
tspan = (0.0, 250.0)
dprob = DiscreteProblem(js, u₀map, tspan, parammap)
```
