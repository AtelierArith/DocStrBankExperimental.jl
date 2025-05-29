```julia
struct NonlinearSystem <: ModelingToolkit.AbstractTimeIndependentSystem
```

非線形方程系。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: システムを定義する方程式のベクター。
  * `states`: 未知の変数。
  * `ps`: パラメータ。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された状態。
  * `jac`: ヤコビ行列。注意: このフィールドは、システムに対して[`calculate_jacobian`](@ref)が呼び出されるまで定義されません。
  * `name`: システムの名前。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期条件および/またはパラメータが`ODEProblem`に提供されない場合に使用するデフォルト値。
  * `connector_type`: システムのタイプ。
  * `metadata`: 下流パッケージで使用されるシステムのメタデータ。
  * `gui_metadata`: MTK GUIのメタデータ。
  * `tearing_state`: 中間のテアリング状態のキャッシュ。
  * `substitutions`: テアリングによって生成された置換。
  * `complete`: モデル`sys`が完全である場合、`sys.x`はもはや名前空間を実行しません。
  * `parent`: 簡略化前の階層的親システム。

# 例

```julia
@variables x y z
@parameters σ ρ β

eqs = [0 ~ σ*(y-x),
       0 ~ x*(ρ-z)-y,
       0 ~ x*y - β*z]
@named ns = NonlinearSystem(eqs, [x,y,z],[σ,ρ,β])
```
