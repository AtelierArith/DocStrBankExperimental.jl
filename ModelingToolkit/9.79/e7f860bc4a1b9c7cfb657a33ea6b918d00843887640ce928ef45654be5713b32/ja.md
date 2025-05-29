```julia
struct JumpSystem{U<:RecursiveArrayTools.ArrayPartition} <: ModelingToolkit.AbstractTimeDependentSystem
```

ジャンププロセスのシステム。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: システムのジャンプ。許可されるタイプは `ConstantRateJump`、`VariableRateJump`、`MassActionJump` です。
  * `iv`: 独立変数、通常は時間です。
  * `unknowns`: システムの状態を表す従属変数。独立変数を含んではいけません。
  * `ps`: システムのパラメータ。独立変数を含んではいけません。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された方程式。
  * `name`: システムの名前。
  * `description`: システムの説明。
  * `systems`: 内部システム。これらはユニークな名前を持つ必要があります。
  * `defaults`: 初期条件やパラメータが `ODEProblem` に提供されていない場合に使用するデフォルト値。
  * `guesses`: 初期条件として使用する推測。
  * `initializesystem`: 初期化を行うためのシステム。
  * `initialization_eqs`: 初期化シーケンス中に強制される追加方程式。
  * `connector_type`: システムのタイプ。
  * `continuous_events`: イベントをモデル化する `Vector{SymbolicContinuousCallback}`。積分器は、ゼロ交差ごとにステップを保証するためにルート探索を使用します。
  * `discrete_events`: イベントをモデル化する `Vector{SymbolicDiscreteCallback}`。与えられた条件が積分ステップの終わりで真であるときに影響を実行する `SciMLBase.DiscreteCallback` の象徴的アナログ。カスタム影響関数を使用して未知の値やパラメータを変更する場合は、`reset_aggregated_jumps!(integrator)` を呼び出すことを確認する必要があります。
  * `parameter_dependencies`: トポロジカルにソートされたパラメータ依存方程式。すべてのシンボルはパラメータであり、LHSは単一のパラメータです。
  * `metadata`: システムのメタデータ。下流のパッケージで使用されます。
  * `gui_metadata`: MTK GUI のメタデータ。
  * `namespacing`: false の場合、`sys.x` は名前空間を持たなくなります。
  * `complete`: true の場合、モデルはこれ以上変更されないことを示します。
  * `index_cache`: 高速なシンボリックインデックスのためのキャッシュデータ。
  * `isscheduled`

# 例

```julia
using ModelingToolkit, JumpProcesses
using ModelingToolkit: t_nounits as t

@parameters β γ
@variables S(t) I(t) R(t)
rate₁   = β*S*I
affect₁ = [S ~ S - 1, I ~ I + 1]
rate₂   = γ*I
affect₂ = [I ~ I - 1, R ~ R + 1]
j₁      = ConstantRateJump(rate₁,affect₁)
j₂      = ConstantRateJump(rate₂,affect₂)
j₃      = MassActionJump(2*β+γ, [R => 1], [S => 1, R => -1])
@named js      = JumpSystem([j₁,j₂,j₃], t, [S,I,R], [β,γ])
```
