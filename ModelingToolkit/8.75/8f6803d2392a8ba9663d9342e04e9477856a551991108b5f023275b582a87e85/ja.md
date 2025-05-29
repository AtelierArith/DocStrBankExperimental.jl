```julia
struct ConstraintsSystem <: ModelingToolkit.AbstractTimeIndependentSystem
```

方程の制約システム。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `constraints`: システムを定義する方程式のベクター。
  * `states`: 不明な変数。
  * `ps`: パラメータ。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された変数。
  * `jac`: ヤコビ行列。注意: このフィールドは、システムに対して[`calculate_jacobian`](@ref)が呼び出されるまで定義されません。
  * `name`: システムの名前。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期条件および/またはパラメータが`ODEProblem`に提供されない場合に使用するデフォルト値。
  * `connector_type`: システムのタイプ。
  * `metadata`: 下流のパッケージで使用されるシステムのメタデータ。
  * `tearing_state`: 中間のティアリング状態のキャッシュ。
  * `substitutions`: ティアリングによって生成された置換。

# 例

```julia
@variables x y z
@parameters a b c

cstr = [0 ~ a*(y-x),
       0 ~ x*(b-z)-y,
       0 ~ x*y - c*z
       x^2 + y^2 ≲ 1]
@named ns = ConstraintsSystem(cstr, [x,y,z],[a,b,c])
```
