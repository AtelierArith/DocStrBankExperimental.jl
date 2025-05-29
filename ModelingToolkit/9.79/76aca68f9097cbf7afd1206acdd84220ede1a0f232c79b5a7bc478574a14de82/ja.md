```julia
struct DiscreteSystem <: ModelingToolkit.AbstractDiscreteSystem
```

差分方程のシステム。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: 離散システムを定義する微分方程式。
  * `iv`: 独立変数。
  * `unknowns`: 従属（状態）変数。独立変数を含んではいけません。
  * `ps`: パラメータ変数。独立変数を含んではいけません。
  * `tspan`: 時間範囲。
  * `var_to_name`: 配列変数。
  * `observed`: 観測された状態。
  * `name`: システムの名前。
  * `description`: システムの説明。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期条件および/またはパラメータが`DiscreteProblem`に提供されていない場合に使用するデフォルト値。
  * `guesses`: 初期条件として使用する推測値。
  * `initializesystem`: 初期化を行うためのシステム。
  * `initialization_eqs`: 初期化シーケンス中に強制される追加の方程式。
  * `preface`: RHS関数の評価前に代入文を挿入します。
  * `connector_type`: システムのタイプ。
  * `parameter_dependencies`: トポロジカルにソートされたパラメータ依存方程式で、すべての記号がパラメータであり、LHSは単一のパラメータです。
  * `metadata`: システムのメタデータで、下流のパッケージで使用されます。
  * `gui_metadata`: MTK GUI用のメタデータ。
  * `tearing_state`: 中間のテアリング状態のキャッシュ。
  * `substitutions`: テアリングによって生成された置換。
  * `namespacing`: falseの場合、`sys.x`はもはや名前空間を実行しません。
  * `complete`: trueの場合、モデルはこれ以上変更されないことを示します。
  * `index_cache`: 高速なシンボリックインデックスのためのキャッシュデータ。
  * `parent`: 簡略化前の階層的な親システム。
  * `isscheduled`

# 例

```
using ModelingToolkit
using ModelingToolkit: t_nounits as t
@parameters σ=28.0 ρ=10.0 β=8/3 δt=0.1
@variables x(t)=1.0 y(t)=0.0 z(t)=0.0
k = ShiftIndex(t)
eqs = [x(k+1) ~ σ*(y-x),
       y(k+1) ~ x*(ρ-z)-y,
       z(k+1) ~ x*y - β*z]
@named de = DiscreteSystem(eqs,t,[x,y,z],[σ,ρ,β]; tspan = (0, 1000.0)) # または
@named de = DiscreteSystem(eqs)
```
