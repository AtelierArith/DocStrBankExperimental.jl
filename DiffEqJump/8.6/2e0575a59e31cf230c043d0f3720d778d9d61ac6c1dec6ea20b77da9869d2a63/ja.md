```julia
struct SSAStepper <: SciMLBase.AbstractDEAlgorithm
```

純粋なジャンプ問題に対する非常に効率的な積分器で、`ConstantRateJump`および/または`MassActionJump`のみを含みます。

## 注意事項

  * `DiscreteProblem`から定義された`JumpProblem`でのみ機能します。
  * `ConstantRateJump`および`MassActionJump`のコレクションでのみ機能します。
  * イベントに対して`DiscreteCallback`のみをサポートします。

## 例

SIRモデル：

```julia
using DiffEqJump
β = 0.1 / 1000.0; ν = .01;
p = (β,ν)
rate1(u,p,t) = p[1]*u[1]*u[2]  # β*S*I
function affect1!(integrator)
  integrator.u[1] -= 1         # S -> S - 1
  integrator.u[2] += 1         # I -> I + 1
end
jump = ConstantRateJump(rate1,affect1!)

rate2(u,p,t) = p[2]*u[2]      # ν*I
function affect2!(integrator)
  integrator.u[2] -= 1        # I -> I - 1
  integrator.u[3] += 1        # R -> R + 1
end
jump2 = ConstantRateJump(rate2,affect2!)
u₀    = [999,1,0]
tspan = (0.0,250.0)
prob = DiscreteProblem(u₀, tspan, p)
jump_prob = JumpProblem(prob, Direct(), jump, jump2)
sol = solve(jump_prob, SSAStepper())
```

詳細については、[チュートリアル](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/)を参照してください。
