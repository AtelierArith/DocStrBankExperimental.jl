```julia
struct JumpSystem{U<:RecursiveArrayTools.ArrayPartition} <: ModelingToolkit.AbstractTimeDependentSystem
```

ジャンププロセスのシステム。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: システムのジャンプ。許可されるタイプは `ConstantRateJump`、`VariableRateJump`、`MassActionJump` です。
  * `iv`: 独立変数、通常は時間。
  * `states`: 従属変数で、システムの状態を表します。独立変数を含んではいけません。
  * `ps`: システムのパラメータ。独立変数を含んではいけません。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された状態。
  * `name`: システムの名前。
  * `systems`: 内部システム。これらはユニークな名前を持つ必要があります。
  * `defaults`: 初期条件やパラメータが `ODEProblem` に提供されていない場合に使用するデフォルト値。
  * `connector_type`: システムのタイプ。
  * `discrete_events`: イベントをモデル化する `Vector{SymbolicDiscreteCallback}`。与えられた条件が統合ステップの終わりで真であるときに影響を実行する `SciMLBase.DiscreteCallback` の象徴的アナログ。状態値やパラメータを変更するカスタム影響関数を使用する場合は、`reset_aggregated_jumps!(integrator)` を呼び出すことを確認する必要があります。
  * `metadata`: 下流パッケージで使用されるシステムのメタデータ。
  * `gui_metadata`: MTK GUI のメタデータ。
  * `complete`: モデル `sys` が完全である場合、`sys.x` はもはや名前空間を実行しません。

# 例

```julia
using ModelingToolkit, JumpProcesses

@parameters β γ
@variables t S(t) I(t) R(t)
rate₁   = β*S*I
affect₁ = [S ~ S - 1, I ~ I + 1]
rate₂   = γ*I
affect₂ = [I ~ I - 1, R ~ R + 1]
j₁      = ConstantRateJump(rate₁,affect₁)
j₂      = ConstantRateJump(rate₂,affect₂)
j₃      = MassActionJump(2*β+γ, [R => 1], [S => 1, R => -1])
@named js      = JumpSystem([j₁,j₂,j₃], t, [S,I,R], [β,γ])
```
