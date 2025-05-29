```
mutable struct IEEEST <: PSS
    input_code::Int
    remote_bus_control::Int
    A1::Float64
    A2::Float64
    A3::Float64
    A4::Float64
    A5::Float64
    A6::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    T5::Float64
    T6::Float64
    Ks::Float64
    Ls_lim::Tuple{Float64, Float64}
    Vcu::Float64
    Vcl::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

IEEE安定化モデルPSS。

# 引数

  * `input_code::Int`: 安定化装置のコード入力、検証範囲: `(1, 6)`
  * `remote_bus_control::Int`: 制御用のACBus識別[`number`](@ref ACBus)。`0`はこのコンポーネントに接続されたバスを識別します
  * `A1::Float64`: フィルター係数、検証範囲: `(0, nothing)`
  * `A2::Float64`: フィルター係数、検証範囲: `(0, nothing)`
  * `A3::Float64`: フィルター係数、検証範囲: `(0, nothing)`
  * `A4::Float64`: フィルター係数、検証範囲: `(0, nothing)`
  * `A5::Float64`: フィルター係数、検証範囲: `(0, nothing)`
  * `A6::Float64`: フィルター係数、検証範囲: `(0, nothing)`
  * `T1::Float64`: 時間定数、検証範囲: `(0, 10)`
  * `T2::Float64`: 時間定数、検証範囲: `(0, 10)`
  * `T3::Float64`: 時間定数、検証範囲: `(0, 10)`
  * `T4::Float64`: 時間定数、検証範囲: `(0, 10)`
  * `T5::Float64`: 時間定数、検証範囲: `(0, 10)`
  * `T6::Float64`: 時間定数、検証範囲: `(eps(), 2.0)`
  * `Ks::Float64`: 比例ゲイン、検証範囲: `(0, nothing)`
  * `Ls_lim::Tuple{Float64, Float64}`: 調整器出力のPSS出力制限 `(Ls_min, Ls_max)`
  * `Vcu::Float64`: カットオフリミッターの上限、検証範囲: `(0, 1.25)`
  * `Vcl::Float64`: カットオフリミッターの下限、検証範囲: `(0, 1.0)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は：

```
x_p1: 1st filter integration,
x_p2: 2nd filter integration, 
x_p3: 3rd filter integration, 
x_p4: 4rd filter integration, 
x_p5: T1/T2 lead-lag integrator, 
x_p6: T3/T4 lead-lag integrator, 
:x_p7 last integer,
```

  * `n_states::Int`: (**変更しないでください。**) IEEESTは7つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) IEEESTは7つの[differential](@ref states_list) [状態](@ref S)を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
