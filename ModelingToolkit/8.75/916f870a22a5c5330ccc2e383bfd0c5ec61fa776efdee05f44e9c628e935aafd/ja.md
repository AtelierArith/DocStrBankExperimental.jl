```julia
struct ODESystem <: ModelingToolkit.AbstractODESystem
```

常微分方程のシステム。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: システムを定義するODE。
  * `iv`: 独立変数。
  * `states`: 従属（状態）変数。独立変数を含んではいけません。

    N.B.: `torn_matching !== nothing` の場合、これにはすべての変数が含まれます。実際のODE状態は、`torn_matching`内の`SelectedState()`エントリによって決定されます。
  * `ps`: パラメータ変数。独立変数を含んではいけません。
  * `tspan`: 時間範囲。
  * `var_to_name`: 配列変数。
  * `ctrls`: 制御パラメータ（`ps`の一部）。
  * `observed`: 観測された状態。
  * `tgrad`: 時間微分行列。注意: このフィールドは、システムに対して[`calculate_tgrad`](@ref)が呼び出されるまで定義されません。
  * `jac`: ヤコビ行列。注意: このフィールドは、システムに対して[`calculate_jacobian`](@ref)が呼び出されるまで定義されません。
  * `ctrl_jac`: 制御ヤコビ行列。注意: このフィールドは、システムに対して[`calculate_control_jacobian`](@ref)が呼び出されるまで定義されません。
  * `Wfact`: 注意: このフィールドは、システムに対して[`generate_factorized_W`](@ref)が呼び出されるまで定義されません。
  * `Wfact_t`: 注意: このフィールドは、システムに対して[`generate_factorized_W`](@ref)が呼び出されるまで定義されません。
  * `name`: システムの名前。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期条件やパラメータが`ODEProblem`に提供されない場合に使用するデフォルト値。
  * `torn_matching`: システムを解決する方法を指定する破断結果。
  * `connector_type`: システムのタイプ。
  * `preface`: RHS関数の評価前に代入文を挿入します。
  * `continuous_events`: イベントをモデル化する`Vector{SymbolicContinuousCallback}`。積分器は、ゼロ交差ごとにステップを保証するためにルート探索を使用します。
  * `discrete_events`: イベントをモデル化する`Vector{SymbolicDiscreteCallback}`。与えられた条件が積分ステップの終わりで真であるときに影響を実行する、`SciMLBase.DiscreteCallback`の象徴的アナログ。
  * `metadata`: 下流パッケージで使用されるシステムのメタデータ。
  * `gui_metadata`: MTK GUIのメタデータ。
  * `tearing_state`: 中間破断状態のキャッシュ。
  * `substitutions`: 破断によって生成された置換。
  * `complete`: モデル`sys`が完全である場合、`sys.x`はもはや名前空間を実行しません。
  * `discrete_subsystems`: 離散サブシステムのリスト。
  * `unknown_states`: ソルバーによって解決される必要がある実際の状態のリスト。ODAEPoblemのみに使用されます。
  * `split_idxs`: 分割パラメータのインデックスのベクトルのベクトル。
  * `parent`: 簡略化前の階層的親システム。

# 例

```julia
using ModelingToolkit

@parameters σ ρ β
@variables t x(t) y(t) z(t)
D = Differential(t)

eqs = [D(x) ~ σ*(y-x),
       D(y) ~ x*(ρ-z)-y,
       D(z) ~ x*y - β*z]

@named de = ODESystem(eqs,t,[x,y,z],[σ,ρ,β],tspan=(0, 1000.0))
```
