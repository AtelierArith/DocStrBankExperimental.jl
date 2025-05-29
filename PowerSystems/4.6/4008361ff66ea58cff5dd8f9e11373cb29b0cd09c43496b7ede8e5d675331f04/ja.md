```
mutable struct ESAC8B <: AVR
    Tr::Float64
    Kp::Float64
    Ki::Float64
    Kd::Float64
    Td::Float64
    Ka::Float64
    Ta::Float64
    Vr_lim::MinMax
    Te::Float64
    Ke::Float64
    E_sat::Tuple{Float64, Float64}
    Se::Tuple{Float64, Float64}
    V_ref::Float64
    saturation_coeffs::Tuple{Float64, Float64}
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

励磁システム AC8B。PSSEにおけるBaslerデジタル励磁制御システム（DECS）をPIDコントローラで表現するために使用されます。

# 引数

  * `Tr::Float64`: レギュレータ入力フィルタの時間定数（秒）、検証範囲: `(0, nothing)`
  * `Kp::Float64`: レギュレータ比例PIDゲイン、検証範囲: `(0, nothing)`
  * `Ki::Float64`: レギュレータ積分PIDゲイン、検証範囲: `(0, nothing)`
  * `Kd::Float64`: レギュレータ微分PIDゲイン、検証範囲: `(0, nothing)`
  * `Td::Float64`: レギュレータ微分PID時間定数、検証範囲: `(0, 10)`
  * `Ka::Float64`: レギュレータ出力ゲイン、検証範囲: `(0, 1000)`
  * `Ta::Float64`: レギュレータ出力遅延時間定数（秒）、検証範囲: `(0, 10)`
  * `Vr_lim::MinMax`: 励磁器フィールド電圧の制限 `(Vr_min, Vr_max)`
  * `Te::Float64`: 励磁器フィールドの時間定数、検証範囲: `(eps(), 2)`
  * `Ke::Float64`: 励磁器フィールドの比例定数、検証範囲: `(0, 2)`
  * `E_sat::Tuple{Float64, Float64}`: 飽和係数に対する励磁器出力電圧: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: 励磁器出力電圧における飽和係数: (Se(E1), Se(E2))
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧セットポイント（pu）、検証範囲: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (デフォルト: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**変更しないでください。**) 関数の係数 (A,B): Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次の通りです:

```
Vm: 感知された端子電圧,
x_i: 内部PIブロック状態,
x_d: 内部微分ブロック状態,
Vr: 電圧レギュレータ状態,
Efd: 励磁器出力状態
```

  * `n_states::Int`: (**変更しないでください。**) ESAC8Bは5つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ESAC8Bは5つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
