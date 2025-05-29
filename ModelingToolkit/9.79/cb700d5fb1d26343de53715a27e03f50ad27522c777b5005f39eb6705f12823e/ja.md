```julia
struct OptimizationSystem <: ModelingToolkit.AbstractOptimizationSystem
```

最適化のためのスカラー方程式。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `op`: システムの目的関数。
  * `unknowns`: 不明な変数。
  * `ps`: パラメータ。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された方程式。
  * `constraints`: システムの制約方程式のリスト。
  * `name`: システムの名前。
  * `description`: システムの説明。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期推測および/またはパラメータが`OptimizationProblem`に提供されていない場合に使用するデフォルト値。
  * `metadata`: 下流パッケージで使用されるシステムのメタデータ。
  * `gui_metadata`: MTK GUIのためのメタデータ。
  * `namespacing`: falseの場合、`sys.x`は名前空間を適用しなくなります。
  * `complete`: trueの場合、モデルはこれ以上変更されないことを示します。
  * `index_cache`: 高速なシンボリックインデックスのためのキャッシュデータ。
  * `parent`: 簡略化前の階層的親システム。
  * `isscheduled`

# 例

```julia
@variables x y z
@parameters a b c

obj = a * (y - x) + x * (b - z) - y + x * y - c * z
cons = [x^2 + y^2 ≲ 1]
@named os = OptimizationSystem(obj, [x, y, z], [a, b, c]; constraints = cons)
```
