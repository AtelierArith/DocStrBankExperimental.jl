`Process`フィールドの各項目の簡単な説明を含む辞書：

  * `process`: 特定のシミュレーションを実行する`Process`型のメソッドを持つ`Function`。例については[NonstationaryProcesses.jl](https://github.com/brendanjohnharris/NonstationaryProcesses.jl)を参照してください。
  * `parameter_profile`: システムの各パラメータが時間とともにどのように変化するかを説明する`Function`のタプル。これらは関数または`:parameter_profile_parameters`で与えられたパラメータのカリー化された関数である可能性があります。例として[`constantParameter`](@ref ParameterProfiles.constantParameter)、[`Discontinuous`](@ref)を参照してください。
  * `parameter_profile_parameters`: 各`:parameter_profile`のためのパラメータのタプル（タプルである可能性もあります）
  * `X0`: システムの変数の数と同じ長さのベクトルとして与えられる初期条件
  * `t0`: シミュレーションの初期時間で、システムが状態`:X0`を持つ時点
  * `transient_t0`: 初期条件`:X0`から`:t0`までのシステムをシミュレーションする時間の長さで、[`timeseries`](@ref)を取得する際に破棄されます
  * `dt`: シミュレーションとソルバーの時間ステップ
  * `savedt`: 解の[`timeseries`](@ref)のサンプリング期間で、`:dt`の倍数でなければなりません
  * `tmax`: シミュレーションの最終時間点。シミュレーションの期間は`:tmax - :transient_t0`であり、返される時系列の期間は`:tmax - :t0`です。[`times`](@ref)を参照してください。
  * `alg`: `DifferentialEquations.jl`プロセスを解くために使用されるアルゴリズム。例えば、[ODE solvers](https://diffeq.sciml.ai/stable/solvers/ode_solve/)のリストを参照してください。
  * `solver_opts`: `:alg`に渡される追加オプションの辞書。これにはソルバーの許容誤差、適応時間ステップ、または最大反復回数が含まれる可能性があります。[一般的なソルバーオプション](https://diffeq.sciml.ai/stable/basics/common_solver_opts/)を参照してください。
  * `solver_rng`: デフォルトでランダムな数に設定された乱数生成器の整数シード
  * `id`: 特定の[`Process`](@ref)のための一意の整数ID
  * `date`: [`Process`](@ref)が作成された日付
  * `solution`: シミュレーションの解をそのネイティブ形式で（例： [ODE solution](https://diffeq.sciml.ai/stable/types/ode_types/#SciMLBase.ODESolution)）
  * `varnames`: [`Process`](@ref)の変数のダミー名で、デフォルトは`[:x, :y, :z, ...]`です。
