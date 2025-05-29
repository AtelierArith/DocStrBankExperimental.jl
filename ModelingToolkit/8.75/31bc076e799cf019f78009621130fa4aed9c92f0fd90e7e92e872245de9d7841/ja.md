```julia
struct OptimizationSystem <: ModelingToolkit.AbstractOptimizationSystem
```

最適化のためのスカラー方程式。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `op`: システムの目的関数。
  * `states`: 不明な変数。
  * `ps`: パラメータ。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された変数。
  * `constraints`: システムの制約方程式のリスト。
  * `name`: システムの名前。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期推測および/またはパラメータが`OptimizationProblem`に提供されていない場合に使用するデフォルト値。
  * `metadata`: 下流パッケージで使用されるシステムのメタデータ。
  * `gui_metadata`: MTK GUIのためのメタデータ。
  * `complete`: モデル`sys`が完全である場合、`sys.x`はもはや名前空間を実行しません。
  * `parent`: 簡略化前の階層的親システム。

# 例

```julia
@variables x y z
@parameters a b c

obj = a * (y - x) + x * (b - z) - y + x * y - c * z
cons = [x^2 + y^2 ≲ 1]
@named os = OptimizationSystem(obj, [x, y, z], [a, b, c]; constraints = cons)
```
