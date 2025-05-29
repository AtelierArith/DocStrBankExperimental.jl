```julia
struct NonlinearSystem <: ModelingToolkit.AbstractTimeIndependentSystem
```

非線形方程系。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: システムを定義する方程式のベクター。
  * `unknowns`: 不明な変数。
  * `ps`: パラメータ。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された方程式。
  * `jac`: ヤコビ行列。注意: このフィールドは、システムに対して[`calculate_jacobian`](@ref)が呼び出されるまで定義されません。
  * `name`: システムの名前。
  * `description`: システムの説明。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期条件および/またはパラメータが`ODEProblem`に提供されない場合に使用するデフォルト値。
  * `guesses`: 初期条件として使用する推測値。
  * `initializesystem`: 初期化を行うためのシステム。
  * `initialization_eqs`: 初期化シーケンス中に強制される追加の方程式。
  * `connector_type`: システムのタイプ。
  * `parameter_dependencies`: トポロジー的にソートされたパラメータ依存方程式で、すべてのシンボルがパラメータであり、LHSが単一のパラメータです。
  * `metadata`: システムのメタデータで、下流のパッケージで使用されます。
  * `gui_metadata`: MTK GUIのメタデータ。
  * `is_initializesystem`: これが初期化システムであるかどうか。
  * `tearing_state`: 中間のテアリング状態のキャッシュ。
  * `substitutions`: テアリングによって生成された置換。
  * `namespacing`: falseの場合、`sys.x`はもはや名前空間を実行しません。
  * `complete`: trueの場合、モデルはこれ以上変更されないことを示します。
  * `index_cache`: 高速なシンボリックインデックスのためのキャッシュデータ。
  * `parent`: 簡略化前の階層的親システム。
  * `isscheduled`

# 例

```julia
@variables x y z
@parameters σ ρ β

eqs = [0 ~ σ*(y-x),
       0 ~ x*(ρ-z)-y,
       0 ~ x*y - β*z]
@named ns = NonlinearSystem(eqs, [x,y,z],[σ,ρ,β])
```
