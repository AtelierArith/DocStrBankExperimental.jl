```julia
struct SSAStepper <: SciMLBase.AbstractDEAlgorithm
```

純粋なジャンプ問題に対する非常に効率的な積分器で、`ConstantRateJump`、`MassActionJump`、および/または*レート境界を持つ* `VariableRateJump` のみを含みます。

## 注意事項

  * `DiscreteProblem` から定義された `JumpProblem` のみで機能します。
  * レート境界を持つ `ConstantRateJump`、`MassActionJump`、および `VariableRateJump` のコレクションでのみ機能します。
  * `SSAStepper` によって取られた各ステップの後にチェックされるイベントのために、`DiscreteCallback` のみをサポートします。
  * 一般的なソルバーインターフェースからの出力制御の限られたサブセット、具体的には `save_start`、`save_end`、および `saveat` のみをサポートします。
  * ODE や SDE でジャンプを使用する場合と同様に、ジャンプが発生するたびに保存するかどうかの制御は、`JumpProblem` への `save_positions` キーワード引数を介して行われます。`SSAStepper` をタイムステッパーとして選択する場合、`save_positions = (true,true)`、`(true,false)`、または `(false,true)` はすべて同等です。`SSAStepper` は、これらの各ケースで解オブジェクトにおいてポストジャンプ状態のみを保存します。これは、`SSAStepper` を介して生成された解オブジェクトが区分定数補間を使用し、ポストジャンプ状態を知るだけでサンプリングされたジャンププロセスのパスを正確に再構築できるためです。つまり、任意の `0 <= t <= tstop` に対して `sol(t)` は、`save_positions` の少なくとも1つのコンポーネントが `true` である場合に、`t` でのサンプリングされた解パスの正確な値を提供します。

## 例

SIRモデル:

```julia
using JumpProcesses
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

詳細については、[チュートリアル](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)を参照してください。
