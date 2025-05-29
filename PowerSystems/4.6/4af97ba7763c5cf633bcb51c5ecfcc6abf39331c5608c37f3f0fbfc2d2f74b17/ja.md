```
mutable struct ESAC6A <: AVR
    Tr::Float64
    Ka::Float64
    Ta::Float64
    Tk::Float64
    Tb::Float64
    Tc::Float64
    Va_lim::MinMax
    Vr_lim::MinMax
    Te::Float64
    VFE_lim::Float64
    Kh::Float64
    VH_max::Float64
    Th::Float64
    Tj::Float64
    Kc::Float64
    Kd::Float64
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

修正された AC6A。システム供給の電子電圧レギュレーターを持つフィールド制御のオルタネーター-整流器励磁システムを表すために使用されます。 IEEE Std 421.5 タイプ AC6A 励磁システムのパラメータ。 PSSE および PSLF における ESAC6A

# 引数

  * `Tr::Float64`: レギュレーター入力フィルターの時間定数（秒）、検証範囲: `(0, 0.5)`
  * `Ka::Float64`: レギュレーター出力ゲイン、検証範囲: `(0, 1000)`
  * `Ta::Float64`: レギュレーター出力遅延時間定数（秒）、検証範囲: `(0, 10)`
  * `Tk::Float64`: 電圧レギュレーターのリード時間定数、検証範囲: `(0, 10)`
  * `Tb::Float64`: レギュレーターの分母（遅延）時間定数（秒）、検証範囲: `(0, 20)`
  * `Tc::Float64`: レギュレーターの分子（リード）時間定数（秒）、検証範囲: `(0, 20)`
  * `Va_lim::MinMax`: レギュレーター出力の制限 `(Va_min, Va_max)`
  * `Vr_lim::MinMax`: 励磁器フィールド電圧の制限 `(Vr_min, Vr_max)`
  * `Te::Float64`: 励磁器フィールドの時間定数、検証範囲: `(eps(), 2)`
  * `VFE_lim::Float64`: 励磁器フィールド電流制限器の基準、検証範囲: `(-5, 20)`
  * `Kh::Float64`: 励磁器フィールド電流レギュレーターのフィードバックゲイン、検証範囲: `(0, 100)`
  * `VH_max::Float64`: 励磁器フィールド電流制限器の最大出力、検証範囲: `(0, 100)`
  * `Th::Float64`: 励磁器フィールド電流制限器の分母（遅延）時間定数、検証範囲: `(0, 1)`
  * `Tj::Float64`: 励磁器フィールド電流制限器の分子（リード）時間定数、検証範囲: `(0, 1)`
  * `Kc::Float64`: 整流器の負荷係数、コミュテーションリアクタンスに比例、検証範囲: `(0, 1)`
  * `Kd::Float64`: 磁気除去係数、励磁器オルタネーターのリアクタンスの関数、検証範囲: `(0, 2)`
  * `Ke::Float64`: 励磁器フィールドの比例定数、検証範囲: `(0, 2)`
  * `E_sat::Tuple{Float64, Float64}`: 飽和係数に対する励磁器出力電圧: (E1, E2)
  * `Se::Tuple{Float64, Float64}`: 励磁器出力電圧における飽和係数: (Se(E1), Se(E2))
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値 (pu)、検証範囲: `(0, nothing)`
  * `saturation_coeffs::Tuple{Float64, Float64}`: (デフォルト: `PowerSystems.get_avr_saturation(E_sat, Se)`) (**変更しないでください。**) 関数の係数 (A,B): Se(V) = B(V - A)^2/V
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための [*ext*ra 辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S) は:

```
Vm: 感知された端子電圧,
Vr1: リード-ラグ状態,
Vr2: レギュレーター出力状態,
Ve: 積分器出力状態,
Vr3: フィードバック出力状態
```

  * `n_states::Int`: (**変更しないでください。**) ESAC6A は 5 つの状態を持ちます
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) ESAC6A は 5 つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照
