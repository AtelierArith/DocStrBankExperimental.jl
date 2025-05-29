```
mutable struct GeneralGovModel <: TurbineGov
    Rselect::Int
    fuel_flag::Int
    R::Float64
    Tpelec::Float64
    speed_error_signal::MinMax
    Kp_gov::Float64
    Ki_gov::Float64
    Kd_gov::Float64
    Td_gov::Float64
    valve_position_limits::MinMax
    T_act::Float64
    K_turb::Float64
    Wf_nl::Float64
    Tb::Float64
    Tc::Float64
    T_eng::Float64
    Tf_load::Float64
    Kp_load::Float64
    Ki_load::Float64
    Ld_ref::Float64
    Dm::Float64
    R_open::Float64
    R_close::Float64
    Ki_mw::Float64
    A_set::Float64
    Ka::Float64
    Ta::Float64
    T_rate::Float64
    db::Float64
    Tsa::Float64
    Tsb::Float64
    R_lim::UpDown
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

GE一般ガバナー/タービンモデル。GeneralGovModel (GGOV1) モデルは、ガスタービンを含む比例-積分-微分 (PID) ガバナーによって制御されるさまざまなプライムムーバーに使用される汎用ガバナーモデルです。

# 引数

  * `Rselect::Int`: ガバナーのドロップのフィードバック信号、検証範囲: `(-2, 1)`
  * `fuel_flag::Int`: 燃料源特性のフラグスイッチ、検証範囲: `(0, 1)`
  * `R::Float64`: スピードドロップパラメータ、検証範囲: `(eps(), nothing)`
  * `Tpelec::Float64`: 電力トランスデューサの時間定数、秒、検証範囲: `(eps(), nothing)`
  * `speed_error_signal::MinMax`: スピードエラー信号の制限
  * `Kp_gov::Float64`: ガバナーの比例ゲイン、検証範囲: `(0, nothing)`
  * `Ki_gov::Float64`: ガバナーの積分ゲイン、検証範囲: `(0, nothing)`
  * `Kd_gov::Float64`: ガバナーの微分ゲイン、検証範囲: `(0, nothing)`
  * `Td_gov::Float64`: ガバナーの微分時間定数、検証範囲: `(0, nothing)`
  * `valve_position_limits::MinMax`: バルブ位置の制限
  * `T_act::Float64`: アクチュエーターの時間定数、検証範囲: `(0, nothing)`
  * `K_turb::Float64`: タービンゲイン、検証範囲: `(0, nothing)`
  * `Wf_nl::Float64`: 無負荷燃料流量、pu、検証範囲: `(0, nothing)`
  * `Tb::Float64`: タービンの遅延時間定数、秒、検証範囲: `(0, nothing)`
  * `Tc::Float64`: タービンの先行時間定数、秒、検証範囲: `(0, nothing)`
  * `T_eng::Float64`: ディーゼルエンジンの輸送遅延時間定数、秒、検証範囲: `(0, nothing)`
  * `Tf_load::Float64`: 負荷リミッターの時間定数、検証範囲: `(0, nothing)`
  * `Kp_load::Float64`: PIコントローラーのための負荷リミッターの比例ゲイン、検証範囲: `(0, nothing)`
  * `Ki_load::Float64`: PIコントローラーのための負荷の積分ゲイン、検証範囲: `(0, nothing)`
  * `Ld_ref::Float64`: PIコントローラーのための負荷リミッターの積分ゲイン、検証範囲: `(0, nothing)`
  * `Dm::Float64`: 機械的ダンピング係数、pu、検証範囲: `(0, nothing)`
  * `R_open::Float64`: 最大バルブ開放率、pu/sec、検証範囲: `(0, nothing)`
  * `R_close::Float64`: 最大バルブ閉鎖率、pu/sec、検証範囲: `(0, nothing)`
  * `Ki_mw::Float64`: 電力コントローラー（リセット）ゲイン、検証範囲: `(0, nothing)`
  * `A_set::Float64`: 加速度リミッターの設定値、pu/sec、検証範囲: `(0, nothing)`
  * `Ka::Float64`: 加速度リミッターのゲイン、検証範囲: `(0, nothing)`
  * `Ta::Float64`: 加速度リミッターの時間定数、検証範囲: `(eps(), nothing)`
  * `T_rate::Float64`: タービンの定格、検証範囲: `(0, nothing)`
  * `db::Float64`: スピードガバナーのデッドバンド、検証範囲: `(0, nothing)`
  * `Tsa::Float64`: 温度検出の先行時間定数、検証範囲: `(0, nothing)`
  * `Tsb::Float64`: 温度検出の遅延時間定数、検証範囲: `(0, nothing)`
  * `R_lim::UpDown`: 負荷増加の最大率
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力設定値 (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) GGOV1モデルの[状態](@ref S)は次のとおりです:

```
Pe: 機械の電力測定,
x_g1: ガバナーの微分制御,
x_g2: ガバナーの積分制御, 
x_g3: タービンアクチュエーター, 
x_g4: タービンの先行-遅延, 
x_g5: タービン負荷リミッターの測定, 
x_g6: タービン負荷リミッターの積分制御, 
x_g7: 監視負荷制御, 
x_g8: 加速度制御, 
x_g9: 温度検出の先行-遅延:
```

  * `n_states::Int`: (**変更しないでください。**) GeneralGovModelは10の状態を持っています
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) GGOV1は10の[differential](@ref states_list) [状態](@ref S)を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
