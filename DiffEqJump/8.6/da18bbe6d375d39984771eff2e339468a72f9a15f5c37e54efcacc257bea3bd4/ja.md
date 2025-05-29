```julia
struct VariableRateJump{R, F, I, T, T2} <: DiffEqJump.AbstractJump
```

時間に明示的に依存するレート（すなわちハザード、強度、または傾向）を持つジャンププロセスを定義します。より正確には、レート関数がジャンプの発生の*間*に変化することが許可されているものです。詳細な例と使用情報については、以下を参照してください。

  * [Tutorial](https://jump.sciml.ai/stable/tutorials/discrete_stochastic_example/)

## フィールド

  * `rate`: ジャンプの現在のレートを返す関数 `rate(u,p,t)`。
  * `affect!`: ジャンプの1回の発生のために状態を更新する関数 `affect(integrator)`。
  * `idxs`
  * `rootfind`
  * `interp_points`
  * `save_positions`
  * `abstol`
  * `reltol`

## 例

`u[1]` が粒子の量を与え、`t*p[1]` が各粒子が消失する確率を時間あたりで示すとします。このジャンププロセスに対応する `VariableRateJump` は次のようになります。

```julia
rate(u,p,t) = t*p[1]*u[1]
affect!(integrator) = integrator.u[1] -= 1
crj = VariableRateJump(rate, affect!)
```

## 注意事項

  * **`VariableRateJump` は `integrator` が主状態ベクトルをラップする効果的な状態タイプを保存することになります。** このオブジェクトの使用に関する詳細は [`ExtendedJumpArray`](@ref) を参照してください。*任意の* `VariableRateJump` が存在する場合、すべての `ConstantRateJump`、`VariableRateJump` およびコールバック `affect!` 関数は `integrator.u` が [`ExtendedJumpArray`](@ref) である `integrator` を受け取ることになります。
  * 正しくシミュレーションするためには `ODEProblem` または `SDEProblem` と共に使用する必要があります（すなわち、現在 `DiscreteProblem` では使用できません）。
  * Salis H., Kaznessis Y.,  Accurate hybrid stochastic simulation of a system of coupled chemical or biochemical reactions, Journal of Chemical Physics, 122 (5), DOI:10.1063/1.1835951 は、ODE/SDE インテグレーター内で `VariableRateJump` を使用してジャンプ時間を計算するために使用されます。
