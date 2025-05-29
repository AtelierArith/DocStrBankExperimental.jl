```
initial_condition_analysis(assembly, t0; kwargs...)
```

初期条件を取得するための分析を実行します。 結果のシステムと、反復手順が収束したかどうかを示すフラグを返します。

# 一般的なキーワード引数

  * `prescribed_conditions = Dict{Int,PrescribedConditions{Float64}}()`:      指定された条件が適用されるポイントに対応するキーを持つ辞書で、      それらのポイントでの指定された条件を説明するタイプ      [`PrescribedConditions`](@ref) の値を持ちます。 時間変化する場合、この入力は      時間の関数として提供されることがあります。
  * `distributed_loads = Dict{Int,DistributedLoads{Float64}}()`: 指定された荷重が      適用される要素に対応するキーを持つ辞書で、      それらの要素に対する分布荷重を説明するタイプ      [`DistributedLoads`](@ref) の値を持ちます。 時間変化する場合、この入力は      時間の関数として提供されることがあります。
  * `point_masses = Dict{Int,PointMass{Float64}}()`: ポイントマスが      取り付けられているポイントに対応するキーを持つ辞書で、      取り付けられたポイントマスの特性を含むタイプ      [`PointMass`](@ref) の値を持ちます。 時間変化する場合、この入力は      時間の関数として提供されることがあります。
  * `linear_velocity = zeros(3)`: ボディフレームの初期線形速度。
  * `angular_velocity = zeros(3)`: ボディフレームの初期角速度。
  * `linear_acceleration = zeros(3)`: ボディフレームの初期線形加速度。
  * `angular_acceleration = zeros(3)`: ボディフレームの初期角加速度。
  * `gravity = [0,0,0]`: 慣性フレームにおける重力ベクトル。

# 制御フラグキーワード引数

  * `reset_state = true`: この分析を実行する前にシステムの状態変数をゼロに設定するかどうかを示すフラグ。
  * `initial_state = nothing`: 初期状態変数を含むタイプ      [`AssemblyState`](@ref) のオブジェクト。 提供されない場合（または`nothing`に設定された場合）、      `system`に保存されている状態変数（デフォルトはゼロ）が初期状態変数として使用されます。
  * `structural_damping = true`: 構造ダンピングを有効にするかどうかを示します。
  * `linear = false`: 線形分析を実行するかどうかを示すフラグ。
  * `two_dimensional = false`: 結果をx-y平面に制約するかどうかを示すフラグ。
  * `steady_state=false`: 定常状態分析を実行して初期化するかどうかを示すフラグ。
  * `show_trace = false`: 解の進行状況を表示するかどうかを示すフラグ。

# 初期条件分析キーワード引数

  * `u0 = fill(zeros(3), length(assembly.points))`: 各ポイントの初期線形変位      **ボディフレームに対して相対的に**
  * `theta0 = fill(zeros(3), length(assembly.points))`: 各ポイントの初期角変位      **ボディフレームに対して相対的に**（ウィーナー・ミレンコビッチパラメータを使用）
  * `V0 = fill(zeros(3), length(assembly.points))`: 各ポイントの初期線形速度      **ボディフレームに対して相対的に**
  * `Omega0 = fill(zeros(3), length(assembly.points))`: 各ポイントの初期角速度      **ボディフレームに対して相対的に**
  * `Vdot0 = fill(zeros(3), length(assembly.points))`: 各ポイントの初期線形加速度      **ボディフレームに対して相対的に**
  * `Omegadot0 = fill(zeros(3), length(assembly.points))`: 各ポイントの初期角加速度      **ボディフレームに対して相対的に**

# 線形分析キーワード引数

  * `update_linearization = false`: 線形分析のために瞬時の状態変数で線形化状態変数を更新するかどうかを示すフラグ。 `false`の場合、初期の状態変数のセットが線形化に使用されます。

# 非線形分析キーワード引数

  * `method = :newton`: 非線形方程式系を解くためのメソッド（NLsolveで定義されている）
  * `linesearch = LineSearches.BackTracking(maxstep=1e6)`: 非線形方程式系を解くために使用されるラインサーチ
  * `ftol = 1e-9`: 非線形方程式系を解くための許容誤差
  * `iterations = 1000`: 非線形方程式系を解くための最大反復回数

# 感度分析キーワード引数

  * `xpfunc = (x, p, t) -> (;)`: `pfunc`に似ていますが、パラメータもGXBeamの状態変数の関数として定義できます。 この関数を使用すると、システムのヤコビアンが自動微分を使用して計算され、非線形ソルバーがニュートン・クリロフソルバー（ラインサーチ付き）に切り替わります。
  * `pfunc = (p, t) -> (;)`: 引数 `assembly`、`prescribed_conditions`、      `distributed_loads`、`point_masses`、`linear_velocity`、`angular_velocity`、      `linear_acceleration`、`angular_acceleration`、`gravity`、`u0`、`theta0`、`V0`、      `Omega0`、`Vdot0`、および `Omegadot0` の更新されたバージョンに対応するフィールドを持つ名前付きタプルを返す関数。 結果の名前付きタプルに含まれるフィールドのみが上書きされます。
  * `p`: キーワード引数 `pfunc` と共に定義された感度パラメータ。 必要ではありませんが、`pfunc` と `p` を使用してこの関数の引数を定義すると、自動微分感度をより効率的に計算できます。
