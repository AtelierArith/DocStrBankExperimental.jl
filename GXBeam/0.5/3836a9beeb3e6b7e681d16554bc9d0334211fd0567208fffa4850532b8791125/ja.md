```
time_domain_analysis(assembly, tvec; kwargs...)
```

`assembly`に含まれる非線形ビームのシステムに対して、時間ベクトル`tvec`を使用して時間領域解析を実行します。最終的なシステム、後処理された解の履歴、および各時間ステップに対して反復手順が収束したかどうかを示す収束フラグを返します。

# 一般的なキーワード引数

  * `prescribed_conditions = Dict{Int,PrescribedConditions{Float64}}()`:      指定された条件が適用されるポイントに対応するキーを持つ辞書で、      それらのポイントでの指定された条件を説明する[`PrescribedConditions`](@ref)のタイプの値を持ちます。      時間変化する場合、この入力は時間の関数として提供できます。
  * `distributed_loads = Dict{Int,DistributedLoads{Float64}}()`:      分布荷重が適用される要素に対応するキーを持つ辞書で、      それらの要素に対する分布荷重を説明する[`DistributedLoads`](@ref)のタイプの値を持ちます。      時間変化する場合、この入力は時間の関数として提供できます。
  * `point_masses = Dict{Int,PointMass{Float64}}()`:      ポイントマスが取り付けられているポイントに対応するキーを持つ辞書で、      取り付けられたポイントマスの特性を含む[`PointMass`](@ref)のタイプの値を持ちます。      時間変化する場合、この入力は時間の関数として提供できます。
  * `linear_velocity = zeros(3)`: ボディフレームの指定された線形速度。
  * `angular_velocity = zeros(3)`: ボディフレームの指定された角速度。
  * `linear_acceleration = zeros(3)`: ボディフレームの初期線形加速度。
  * `angular_acceleration = zeros(3)`: ボディフレームの初期角加速度。
  * `gravity = [0,0,0]`: ボディフレームにおける重力ベクトル。時間変化する場合、この入力は時間の関数として提供できます。

# 制御フラグキーワード引数

  * `reset_state = true`: この解析を実行する前にシステム状態変数をゼロに設定するかどうかを示すフラグ。
  * `initial_state = nothing`: 解析に対応する初期状態と状態率を定義する`AssemblyState`のタイプのオブジェクト。デフォルトでは、この入力は`steady_state_analysis`または`initial_condition_analysis`を使用して計算されます。
  * `steady_state = false`: `initial_state`に対応する状態変数を`steady_state_analysis`を使用して計算するかどうかを示すフラグ（`initial_condition_analysis`ではなく）。
  * `structural_damping = true`: 構造ダンピングを有効にするかどうかを示すフラグ。
  * `linear = false`: 線形解析を実行するかどうかを示すフラグ。
  * `two_dimensional = false`: 結果をx-y平面に制約するかどうかを示すフラグ。
  * `show_trace = false`: 解の進行状況を表示するかどうかを示すフラグ。
  * `save = eachindex(tvec)`: 時間履歴を保存するステップ。

# 初期条件解析引数

  * `u0 = fill(zeros(3), length(assembly.points))`: ボディフレーム内の各ポイントの初期線形変位。
  * `theta0 = fill(zeros(3), length(assembly.points))`: ボディフレーム内の各ポイントの初期角変位（ウィーナー・ミレンコビッチパラメータを使用）。
  * `V0 = fill(zeros(3), length(assembly.points))`: ボディフレーム内の各ポイントの初期線形速度 **ボディフレームの動きからの寄与を除く**。
  * `Omega0 = fill(zeros(3), length(assembly.points))`: ボディフレーム内の各ポイントの初期角速度 **ボディフレームの動きからの寄与を除く**。
  * `Vdot0 = fill(zeros(3), length(assembly.points))`: ボディフレーム内の各ポイントの初期線形加速度 **ボディフレームの動きからの寄与を除く**。
  * `Omegadot0 = fill(zeros(3), length(assembly.points))`: ボディフレーム内の各ポイントの初期角加速度 **ボディフレームの動きからの寄与を除く**。

# 線形解析キーワード引数

  * `update_linearization = false`: 線形解析のために瞬時の状態変数で線形化状態変数を更新するかどうかを示すフラグ。`false`の場合、初期の状態変数のセットが線形化に使用されます。

# 非線形解析キーワード引数

  * `method = :newton`: 非線形方程式系を解くためのメソッド（NLsolveで定義されている）。
  * `linesearch = LineSearches.BackTracking(maxstep=1e6)`: 非線形方程式系を解くために使用されるラインサーチ。
  * `ftol = 1e-9`: 非線形方程式系を解くための許容誤差。
  * `iterations = 1000`: 非線形方程式系を解くための最大反復回数。

# 感度解析キーワード引数

  * `xpfunc = (x, p, t) -> (;)`: `pfunc`に似ていますが、パラメータはGXBeamの状態変数の関数としても定義できます。この関数を使用すると、システムのヤコビアンが自動微分を使用して計算され、非線形ソルバーがニュートン-クリロフソルバー（ラインサーチ付き）に切り替わります。
  * `pfunc = (p, t) -> (;)`: 引数`assembly`、`prescribed_conditions`、`distributed_loads`、`point_masses`、`linear_velocity`、`angular_velocity`、`linear_acceleration`、`angular_acceleration`、`gravity`、`u0`、`theta0`、`V0`、`Omega0`、`Vdot0`、および`Omegadot0`の更新バージョンに対応するフィールドを持つ名前付きタプルを返す関数。結果の名前付きタプルに含まれるフィールドのみが上書きされます。
  * `p`: 感度パラメータ。`pfunc`と共に定義されます。必須ではありませんが、`pfunc`と`p`を使用してこの関数の引数を定義することで、自動微分感度をより効率的に計算できます。
