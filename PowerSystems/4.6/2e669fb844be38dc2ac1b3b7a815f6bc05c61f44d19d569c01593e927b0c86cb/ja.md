```
mutable struct RenewableEnergyConverterTypeA <: Converter
    T_g::Float64
    Rrpwr::Float64
    Brkpt::Float64
    Zerox::Float64
    Lvpl1::Float64
    Vo_lim::Float64
    Lv_pnts::MinMax
    Io_lim::Float64
    T_fltr::Float64
    K_hv::Float64
    Iqr_lims::MinMax
    Accel::Float64
    Lvpl_sw::Int
    Q_ref::Float64
    R_source::Float64
    X_source::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
end
```

再生可能エネルギー発電機/コンバータモデルのパラメータであり、このモデルはPSSEのREGCA1に対応します。

# 引数

  * `T_g::Float64`: コンバータの時間定数 (s)、検証範囲: `(0, nothing)`
  * `Rrpwr::Float64`: 低電圧パワーロジック (LVPL) ランプレート制限 (pu/s)、検証範囲: `(0, nothing)`
  * `Brkpt::Float64`: LVPL特性電圧2 (pu)、検証範囲: `(0, nothing)`
  * `Zerox::Float64`: LVPL特性電圧1 (pu)、検証範囲: `(0, nothing)`
  * `Lvpl1::Float64`: LVPLゲイン (pu)、検証範囲: `(0, nothing)`
  * `Vo_lim::Float64`: 高電圧無効電流管理のための電圧制限 (pu)、検証範囲: `(0, nothing)`
  * `Lv_pnts::MinMax`: 低電圧有効電流管理のための電圧ポイント (pu) (Lvpnt0, Lvpnt1)
  * `Io_lim::Float64`: 高電圧無効電流管理のための電流制限 (pu) (負の値として指定)、検証範囲: `(nothing, 0)`
  * `T_fltr::Float64`: 低電圧有効電流管理のための電圧フィルター時間定数 (s)、検証範囲: `(0, nothing)`
  * `K_hv::Float64`: 高電圧無効電流管理に使用される過電圧補償ゲイン、検証範囲: `(0, nothing)`
  * `Iqr_lims::MinMax`: 無効電流の変化率の制限 (pu/s) (Iqr*min, Iqr*max)
  * `Accel::Float64`: 加速度係数、検証範囲: `(0, 1)`
  * `Lvpl_sw::Int`: 低電圧パワーロジック (LVPL) スイッチ。 (0: LVPLなし、1: LVPLあり)、検証範囲: `(0, 1)`
  * `Q_ref::Float64`: (デフォルト: `1.0`) 力学的電力の初期条件、検証範囲: `(0, nothing)`
  * `R_source::Float64`: (デフォルト: `0.0`) テブナン等価に使用される出力抵抗、検証範囲: `(0, nothing)`
  * `X_source::Float64`: (デフォルト: `1.0e5`) テブナン等価に使用される出力リアクタンス、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [states](@ref S) は:	Ip: Ipcmdのためのコンバータ遅延、	Iq: Iqcmdのためのコンバータ遅延、	Vmeas: 低電圧有効電流管理のための電圧フィルター
  * `n_states::Int`: (**変更しないでください。**) RenewableEnergyConverterTypeAは3つの状態を持ちます
