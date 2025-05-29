```julia
struct ODESystem <: ModelingToolkit.AbstractODESystem
```

常微分方程のシステム。

# フィールド

  * `tag`: システムのタグ。同じタグを持つ2つのシステムは、構造的に同一です。
  * `eqs`: システムを定義するODE。
  * `iv`: 独立変数。
  * `unknowns`: 従属（未知）変数。独立変数を含んではいけません。

    N.B.: `torn_matching !== nothing` の場合、これにはすべての変数が含まれます。実際のODEの未知数は、`torn_matching`内の`SelectedState()`エントリによって決定されます。
  * `ps`: パラメータ変数。独立変数を含んではいけません。
  * `tspan`: 時間範囲。
  * `var_to_name`: 配列変数。
  * `ctrls`: 制御パラメータ（`ps`の一部）。
  * `observed`: 観測された方程式。
  * `constraintsystem`: システムの解によって満たされなければならない制約のシステム。
  * `costs`: 最適制御のためのシステムのコストを定義する式のセット。
  * `consolidate`: コストベクトルを受け取り、最適化のためのスカラーを返します。
  * `tgrad`: 時間微分行列。注意: このフィールドは、システムに対して[`calculate_tgrad`](@ref)が呼び出されるまで定義されません。
  * `jac`: ヤコビ行列。注意: このフィールドは、システムに対して[`calculate_jacobian`](@ref)が呼び出されるまで定義されません。
  * `ctrl_jac`: 制御ヤコビ行列。注意: このフィールドは、システムに対して[`calculate_control_jacobian`](@ref)が呼び出されるまで定義されません。
  * `Wfact`: 注意: このフィールドは、システムに対して[`generate_factorized_W`](@ref)が呼び出されるまで定義されません。
  * `Wfact_t`: 注意: このフィールドは、システムに対して[`generate_factorized_W`](@ref)が呼び出されるまで定義されません。
  * `name`: システムの名前。
  * `description`: システムの説明。
  * `systems`: 内部システム。これらは一意の名前を持つ必要があります。
  * `defaults`: 初期条件やパラメータが`ODEProblem`に提供されない場合に使用するデフォルト値。
  * `guesses`: 初期条件として使用する推測。
  * `torn_matching`: システムを解決する方法を指定する破断結果。
  * `initializesystem`: 初期化を行うためのシステム。
  * `initialization_eqs`: 初期化シーケンス中に強制される追加方程式。
  * `schedule`: コード生成プロセスのスケジュール。
  * `connector_type`: システムのタイプ。
  * `preface`: RHS関数の評価前に代入文を挿入します。
  * `continuous_events`: イベントをモデル化する`Vector{SymbolicContinuousCallback}`。積分器は、各ゼロ交差でステップを保証するためにルート探索を使用します。
  * `discrete_events`: イベントをモデル化する`Vector{SymbolicDiscreteCallback}`。与えられた条件が積分ステップの終わりで真であるときに影響を実行する`SciMLBase.DiscreteCallback`の象徴的アナログ。
  * `parameter_dependencies`: トポロジカルにソートされたパラメータ依存方程式。すべてのシンボルはパラメータであり、LHSは単一のパラメータです。
  * `assertions`: 解決プロセス全体で真であるべき条件のマッピングと、それに対応するエラーメッセージ。これらは`debug_system`を呼び出すときに方程式に追加されます。
  * `metadata`: 下流パッケージで使用されるシステムのメタデータ。
  * `gui_metadata`: MTK GUIのメタデータ。
  * `is_dde`: 与えられた`ODESystem`がDDEのシステムを表すかどうかを示すブール値。
  * `tstops`: ソルバーに提供するためのポイントのリスト。離散イベントと同じ構文を使用します。
  * `tearing_state`: 中間破断状態のキャッシュ。
  * `substitutions`: 破断によって生成された置換。
  * `namespacing`: falseの場合、`sys.x`はもはや名前空間を実行しません。
  * `complete`: trueの場合、モデルはこれ以上変更されないことを示します。
  * `index_cache`: 高速なシンボリックインデックスのためのキャッシュデータ。
  * `discrete_subsystems`: 離散サブシステムのリスト。
  * `solved_unknowns`: ソルバーによって解決される必要がある実際の未知数のリスト。
  * `split_idxs`: 分割パラメータのインデックスのベクトルのベクトル。
  * `ignored_connections`: 変換によって削除された分析ポイントで、無視される接続を表します。タプルの最初の要素はシステムを接続する分析ポイントで、2番目の要素は変数を接続するもの（`connect`の自明な形式のため）。
  * `parent`: 簡略化前の階層的親システム。

# 例

```julia
using ModelingToolkit
using ModelingToolkit: t_nounits as t, D_nounits as D

@parameters σ ρ β
@variables x(t) y(t) z(t)

eqs = [D(x) ~ σ*(y-x),
       D(y) ~ x*(ρ-z)-y,
       D(z) ~ x*y - β*z]

@named de = ODESystem(eqs,t,[x,y,z],[σ,ρ,β],tspan=(0, 1000.0))
```
