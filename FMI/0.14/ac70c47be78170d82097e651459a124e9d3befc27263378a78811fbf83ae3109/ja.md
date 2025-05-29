```
simulate(fmu, instance=nothing, tspan=nothing; kwargs...)
simulate(fmu, tspan; kwargs...)
simulate(instance, tspan; kwargs...)
```

`FMU2`のインスタンス化されたタイプ（CS、ME、またはSE）のシミュレーションを開始します（これは自動的に選択されるか、FMUの読み込み中に選択されます）。特定のシミュレーションモードを強制するには、[`simulateCS`](@ref)、[`simulateME`](@ref)、または[`simulateSE`](@ref)を直接呼び出します。

# 引数

  * `fmu::FMU`: シミュレーションするFMU。
  * `c::Union{FMUInstance, Nothing}=nothing`: FMUのインスタンス（FMI3）またはコンポーネント（FMI2）、利用できない場合は`nothing`。
  * `tspan::Union{Tuple{Float64, Float64}, Nothing}=nothing`: シミュレーション時間範囲をタプルとして指定（デフォルト = nothing: FMUのモデル記述からのデフォルト値を使用するか、指定されていない場合は(0.0, 1.0)）

# キーワード引数

  * `recordValues::fmi2ValueReferenceFormat` = nothing: 記録する変数の配列（文字列または変数識別子）。結果は`DiffEqCallbacks.SavedValues`として返されます。
  * `saveat = nothing`: 値を保存する時間点（補間された値）（デフォルト = nothing: 各ソルバのタイムステップで保存）
  * `setup::Bool`: シミュレーションの前にfmi2SetupExperiment、fmi2EnterInitializationMode、およびfmi2ExitInitializationModeを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `reset::Bool`: 各シミュレーションの前にfmi2Resetを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `instantiate::Bool`: 新しく作成されたインスタンスでfmi2Instantiate!を呼び出してシミュレートする（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `freeInstance::Bool`: シミュレーションの終了時にfmi2FreeInstanceを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `terminate::Bool`: シミュレーションの終了時にfmi2Terminateを呼び出す（デフォルト = nothing: `fmu`の`FMUExecutionConfiguration`からの値を使用）
  * `inputValueReferences::fmi2ValueReferenceFormat = nothing`: 各シミュレーションステップで設定する入力変数（文字列または変数識別子）
  * `inputFunction = nothing`: 各シミュレーションステップで入力変数の値を取得する関数。
  * `parameters::Union{Dict{<:Any, <:Any}, Nothing} = nothing`: 初期化中にパラメータを設定するためのパラメータ変数（文字列または変数識別子）と値（実数、整数、ブール値、文字列）の辞書
  * `showProgress::Bool = true`: REPLにシミュレーション進行状況メーターを表示

## 入力関数パターン

[`c`: 現在のコンポーネント, `u`: 現在の状態, `t`: 現在の時間, `fmi2SetReal(..., inputValueReferences, inputFunction(...))`または`fmi3SetFloat64`に渡される値の配列を返す]:

  * `inputFunction(t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, u::AbstractVector{<:Real})`
  * `inputFunction(x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`
  * `inputFunction(c::Union{FMUInstance, Nothing}, x::AbstractVector{<:Real}, t::Real, u::AbstractVector{<:Real})`

# 戻り値:

  * [`FMUSolution`](@ref)構造体。

[`simulate`](@ref)、[`simulateME`](@ref)、[`simulateCS`](@ref)、[`simulateSE`](@ref)も参照してください。
