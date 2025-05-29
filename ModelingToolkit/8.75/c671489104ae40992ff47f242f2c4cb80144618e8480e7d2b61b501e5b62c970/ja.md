```julia
DiffEqBase.DiscreteProblem(sys::JumpSystem, u0map, tspan,
                           parammap = DiffEqBase.NullParameters;
                           use_union = false,
                           kwargs...)
```

純粋なジャンプJumpSystemのための空のDiscreteProblemを生成し、`prob.prob`として利用します。これは、システムに関連するODEやSDEがない場合に使用されます。

[`JumpSystem`](@ref)の定義からの例を続けます：

```julia
using DiffEqBase, JumpProcesses
u₀map = [S => 999, I => 1, R => 0]
parammap = [β => 0.1 / 1000, γ => 0.01]
tspan = (0.0, 250.0)
dprob = DiscreteProblem(js, u₀map, tspan, parammap)
```
