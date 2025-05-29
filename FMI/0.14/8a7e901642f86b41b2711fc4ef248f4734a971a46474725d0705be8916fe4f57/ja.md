```
simulateME(fmu, instance=nothing, tspan=nothing; kwargs...)
simulateME(fmu, tspan; kwargs...)
simulateME(instance, tspan; kwargs...)
```

指定されたシミュレーション時間間隔のためにME-FMUをシミュレートします。状態イベントと時間イベントは正しく処理されます。

# 引数

  * `fmu::FMU`: シミュレートするFMU。
  * `c::Union{FMUInstance, Nothing}=nothing`: FMUのインスタンス（FMI3）またはコンポーネント（FMI2）、利用できない場合は`nothing`。
  * `tspan::Union{Tuple{Float64, Float64}, Nothing}=nothing`: シミュレーション時間範囲をタプルとして指定（デフォルト = nothing: FMUのモデル記述からのデフォルト値を使用するか、指定されていない場合は(0.0, 1.0)）

# キーワード引数

  * `solver = nothing`: 任意のJuliaサポートのODEソルバー（デフォルト = nothing: DifferentialEquations.jlのデフォルトソルバーを使用）
  * `recordValues::fmi2ValueReferenceFormat` = nothing: 記録する変数の配列（文字列または変数識別子）。結果は`DiffEqCallbacks.SavedValues`として返されます。
  * `recordEventIndicators::Union{AbstractArray{<:Integer, 1}, UnitRange{<:Integer}, Nothing} = nothing`: 記録するイベントインジケーターの配列または範囲
  * `recordEigenvalues::Bool=false`: 固有値を計算して記録
  * `saveat = nothing`: 値を保存する時間点（補間された値）（デフォルト = nothing: 各ソルバーのタイムステップで保存）
  * `x0::Union{AbstractArray{<:Real}, Nothing} = nothing`: 初期fmu状態（デフォルト = nothing: 現在のまたはデフォルト初期fmu状態を使用）
  * `setup::Bool`: シミュレーションの前にfmi2SetupExperiment、fmi2EnterInitializationMode、およびfmi2ExitInitializationModeを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `reset::Bool`: シミュレーションの前にfmi2Resetを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `instantiate::Bool`: 新しく作成されたインスタンスでfmi2Instantiate!を呼び出してシミュレート（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `freeInstance::Bool`: シミュレーションの最後にfmi2FreeInstanceを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `terminate::Bool`: シミュレーションの最後にfmi2Terminateを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `inputValueReferences::fmi2ValueReferenceFormat = nothing`: 各シミュレーションステップで設定する入力変数（文字列または変数識別子）
  * `inputFunction = nothing`: 各シミュレーションステップで入力変数の値を取得するための関数。
  * `parameters::Union{Dict{<:Any, <:Any}, Nothing} = nothing`: 初期化中にパラメータを設定するためのパラメータ変数（文字列または変数識別子）と値（実数、整数、ブール値、文字列）の辞書
  * `callbacksBefore = []`: 状態イベントおよび時間イベントの内部コールバックが呼び出される*前*に呼び出すコールバック
  * `callbacksAfter = []`: 状態イベントおよび時間イベントの内部コールバックが呼び出される*後*に呼び出すコールバック
  * `showProgress::Bool = true`: REPLにシミュレーション進行状況メーターを表示
  * `solveKwargs...`: ソルバーの解呼び出しに渡されるキーワード引数

## 入力関数パターン

[`c`: 現在のコンポーネント, `u`: 現在の状態, `t`: 現在の時間, `fmi2SetReal(..., inputValueReferences, inputFunction(...))`または`fmi3SetFloat64`に渡される値の配列を返す]:

  * `inputFunction(t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, u::AbstractVector{<:Real})`
  * `inputFunction(x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`

# 戻り値:

  * [`FMUSolution`](@ref) 構造体。

他に[`simulate`](@ref)、[`simulateCS`](@ref)、[`simulateSE`](@ref)も参照してください。
