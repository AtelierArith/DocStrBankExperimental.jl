```julia
DiffEqBase.ODEProblem(sys::JumpSystem, u0map, tspan,
                           parammap = DiffEqBase.NullParameters;
                           kwargs...)
```

純粋なジャンプJumpSystemのための空のODEProblemを生成し、`prob.prob`として利用します。これは、システムに関連するODEやSDEがなく、明示的な時間依存性を持つジャンプ（すなわち`VariableRateJump`）がある場合に使用されます。明示的な時間依存性を持つジャンプがない場合、すなわちすべてが`ConstantRateJump`または`MassActionJump`である場合は、パフォーマンスの理由から`DiscreteProblem`が推奨されます。

[`JumpSystem`](@ref)の定義からの例を続けます：

```julia
using DiffEqBase, JumpProcesses
u₀map = [S => 999, I => 1, R => 0]
parammap = [β => 0.1 / 1000, γ => 0.01]
tspan = (0.0, 250.0)
oprob = ODEProblem(complete(js), u₀map, tspan, parammap)
```
