```julia
struct JumpSet{T1, T2, T3, T4} <: JumpProcesses.AbstractJump
```

シミュレーションに含めるべきジャンプのコレクションを定義します。

## フィールド

  * `variable_jumps`: [`VariableRateJump`](@ref)のコレクション
  * `constant_jumps`: [`ConstantRateJump`](@ref)のコレクション
  * `regular_jump`: [`RegularJump`](@ref)のコレクション
  * `massaction_jump`: [`MassActionJump`](@ref)のコレクション

## 例

ここでは、2つのジャンプを構築し、それらを`JumpSet`に格納し、結果として得られるプロセスをシミュレートします。

```julia
using JumpProcesses, OrdinaryDiffEq

rate1(u,p,t) = p[1]
affect1!(integrator) = (integrator.u[1] += 1)
crj = ConstantRateJump(rate1, affect1!)

rate2(u,p,t) = (t/(1+t))*p[2]*u[1]
affect2!(integrator) = (integrator.u[1] -= 1)
vrj = VariableRateJump(rate2, affect2!)

jset = JumpSet(crj, vrj)

f!(du,u,p,t) = (du .= 0)
u0 = [0.0]
p = (20.0, 2.0)
tspan = (0.0, 200.0)
oprob = ODEProblem(f!, u0, tspan, p)
jprob = JumpProblem(oprob, Direct(), jset)
sol = solve(jprob, Tsit5())
```
