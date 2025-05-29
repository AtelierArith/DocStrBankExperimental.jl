```julia
struct DiscreteSystem <: ModelingToolkit.AbstractTimeDependentSystem
```

差分方程のシステム。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: 離散システムを定義する微分方程式。
  * `iv`: 独立変数。
  * `states`: 従属（状態）変数。独立変数を含んではいけません。
  * `ps`: パラメータ変数。独立変数を含んではいけません。
  * `tspan`: 時間範囲。
  * `var_to_name`: 配列変数。
  * `ctrls`: 制御パラメータ（`ps`の一部）。
  * `observed`: 観測された状態。
  * `name`: システムの名前。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期条件および/またはパラメータが`DiscreteProblem`に提供されていない場合に使用するデフォルト値。
  * `preface`: RHS関数の評価前に代入文を挿入します。
  * `connector_type`: システムのタイプ。
  * `metadata`: システムのメタデータで、下流のパッケージで使用されます。
  * `gui_metadata`: MTK GUI用のメタデータ。
  * `tearing_state`: 中間のテアリング状態のキャッシュ。
  * `substitutions`: テアリングによって生成された置換。
  * `complete`: モデル`sys`が完全である場合、`sys.x`はもはや名前空間を実行しません。
  * `parent`: 簡略化前の階層的親システム。

# 例

```
using ModelingToolkit

@parameters σ=28.0 ρ=10.0 β=8/3 δt=0.1
@variables t x(t)=1.0 y(t)=0.0 z(t)=0.0
D = Difference(t; dt=δt)

eqs = [D(x) ~ σ*(y-x),
       D(y) ~ x*(ρ-z)-y,
       D(z) ~ x*y - β*z]

@named de = DiscreteSystem(eqs,t,[x,y,z],[σ,ρ,β]; tspan = (0, 1000.0)) # または
@named de = DiscreteSystem(eqs)
```
