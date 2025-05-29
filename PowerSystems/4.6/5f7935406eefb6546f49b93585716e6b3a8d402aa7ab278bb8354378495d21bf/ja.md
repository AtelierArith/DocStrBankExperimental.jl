```
mutable struct PSS2C <: PSS
    input_code_1::Int
    remote_bus_control_1::Int
    input_code_2::Int
    remote_bus_control_2::Int
    M_rtf::Int
    N_rtf::Int
    Tw1::Float64
    Tw2::Float64
    T6::Float64
    Tw3::Float64
    Tw4::Float64
    T7::Float64
    Ks2::Float64
    Ks3::Float64
    T8::Float64
    T9::Float64
    Ks1::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    T10::Float64
    T11::Float64
    Vs1_lim::Tuple{Float64, Float64}
    Vs2_lim::Tuple{Float64, Float64}
    Vst_lim::Tuple{Float64, Float64}
    T12::Float64
    T13::Float64
    PSS_Hysteresis_param::Tuple{Float64, Float64}
    Xcomp::Float64
    Tcomp::Float64
    hysteresis_binary_logic::Int
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

IEEE 421.5 2016 PSS2C IEEE Dual-Input Stabilizer Model

# 引数

  * `input_code_1::Int`: スタビライザの最初の入力コード、検証範囲: `(1, 7)`
  * `remote_bus_control_1::Int`: 制御用の最初の入力リモートバス識別 [`number`](@ref ACBus)。 `0` はこのコンポーネントに接続されたローカルバスを識別します
  * `input_code_2::Int`: スタビライザの2番目の入力コード、検証範囲: `(1, 6)`
  * `remote_bus_control_2::Int`: 制御用の2番目の入力リモートバス識別 [`number`](@ref ACBus)。 `0` はこのコンポーネントに接続されたローカルバスを識別します
  * `M_rtf::Int`: ランプトラッキングフィルタのMパラメータ、検証範囲: `(0, 8)`
  * `N_rtf::Int`: ランプトラッキングフィルタのNパラメータ、検証範囲: `(0, 8)`
  * `Tw1::Float64`: 最初の入力用の最初のウォッシュアウトフィルタの時間定数、検証範囲: `(eps(), nothing)`
  * `Tw2::Float64`: 最初の入力用の2番目のウォッシュアウトフィルタの時間定数、検証範囲: `(0, nothing)`
  * `T6::Float64`: 最初の入力用のローパスフィルタの時間定数、検証範囲: `(0, nothing)`
  * `Tw3::Float64`: 2番目の入力用の最初のウォッシュアウトフィルタの時間定数、検証範囲: `(eps(), nothing)`
  * `Tw4::Float64`: 2番目の入力用の2番目のウォッシュアウトフィルタの時間定数、検証範囲: `(0, nothing)`
  * `T7::Float64`: 2番目の入力用のローパスフィルタの時間定数、検証範囲: `(0, nothing)`
  * `Ks2::Float64`: 2番目の入力用のローパスフィルタのゲイン、検証範囲: `(0, nothing)`
  * `Ks3::Float64`: 2番目の入力用のゲイン、検証範囲: `(0, nothing)`
  * `T8::Float64`: ランプトラッキングフィルタの時間定数、検証範囲: `(0, nothing)`
  * `T9::Float64`: ランプトラッキングフィルタの時間定数、検証範囲: `(eps(), nothing)`
  * `Ks1::Float64`: リードラグブロックの前のゲイン、検証範囲: `(0, nothing)`
  * `T1::Float64`: 最初のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `T2::Float64`: 最初のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `T3::Float64`: 2番目のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `T4::Float64`: 2番目のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `T10::Float64`: 3番目のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `T11::Float64`: 3番目のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `Vs1_lim::Tuple{Float64, Float64}`: 最初の入力制限 `(Vs1_min, Vs1_max)`
  * `Vs2_lim::Tuple{Float64, Float64}`: 2番目の入力制限 `(Vs2_min, Vs2_max)`
  * `Vst_lim::Tuple{Float64, Float64}`: PSS出力制限 `(Vst_min, Vst_max)`
  * `T12::Float64`: 4番目のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `T13::Float64`: 4番目のリードラグブロックの時間定数、検証範囲: `(0, nothing)`
  * `PSS_Hysteresis_param::Tuple{Float64, Float64}`: PSS出力ヒステリシスパラメータ `(PSSOFF, PSSON)`
  * `Xcomp::Float64`: ステータ漏れリアクタンス、検証範囲: `(0, nothing)`
  * `Tcomp::Float64`: 補償周波数で測定された時間、検証範囲: `(eps(), nothing)`
  * `hysteresis_binary_logic::Int`: (デフォルト: `1`) ヒステリシスメモリ変数
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための [*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S) は:

```
x_p1: 1st washout 1st input, 
x_p2: 2nd washout 1st input, 
x_p3: transducer 1st input, 
x_p4: 1st washout 2nd input, 
x_p5: 2nd washout 2nd input, 
x_p6: transducer 2nd input, 
x_p7: ramp tracking filter state 1, 
x_p8: ramp tracking filter state 2, 
x_p9: ramp tracking filter state 3, 
x_p10: ramp tracking filter state 4, 
x_p11: ramp tracking filter state 5, 
x_p12: ramp tracking filter state 6, 
x_p13: ramp tracking filter state 7, 
x_p14: ramp tracking filter state 8, 
x_p15: 1st lead-lag, 
x_p16: 2nd lead-lag, 
x_p17: 3rd lead-lag, 
x_p18: 4th lead-lag, 
x_p19: washout block for compensated frequency,
```

  * `n_states::Int`: (**変更しないでください。**) IEEESTは19の状態を持っています
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) IEEESTは19の [微分](@ref states_list) [状態](@ref S) を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
