```
mutable struct IEEETurbineGov1 <: TurbineGov
    K::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    U0::Float64
    U_c::Float64
    valve_position_limits::MinMax
    T4::Float64
    K1::Float64
    K2::Float64
    T5::Float64
    K3::Float64
    K4::Float64
    T6::Float64
    K5::Float64
    K6::Float64
    T7::Float64
    K7::Float64
    K8::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

IEEEタイプ1スピードガバーモデル

# 引数

  * `K::Float64`: ガバーレート、検証範囲: `(5, 30)`
  * `T1::Float64`: 入力フィルタ遅延、検証範囲: `(0, 5)`
  * `T2::Float64`: 入力フィルタ先行、検証範囲: `(0, 10)`
  * `T3::Float64`: バルブ位置の時間定数、検証範囲: `(eps(), 1)`
  * `U0::Float64`: 最大バルブ開閉率、検証範囲: `(0.01, 0.03)`
  * `U_c::Float64`: 最大バルブ閉じる率、検証範囲: `(-0.3, 0)`
  * `valve_position_limits::MinMax`: MWにおけるバルブ位置の制限
  * `T4::Float64`: 入力蒸気の時間定数、検証範囲: `(0, 1)`
  * `K1::Float64`: 高圧シャフトパワーの割合、検証範囲: `(-2, 1)`
  * `K2::Float64`: 低圧シャフトパワーの割合、検証範囲: `(0, nothing)`
  * `T5::Float64`: 第二ボイラー通過の時間定数、検証範囲: `(0, 10)`
  * `K3::Float64`: 第二ボイラー通過の高圧シャフトパワーの割合、検証範囲: `(0, 0.5)`
  * `K4::Float64`: 第二ボイラー通過の低圧シャフトパワーの割合、検証範囲: `(0, 0.5)`
  * `T6::Float64`: 第三ボイラー通過の時間定数、検証範囲: `(0, 10)`
  * `K5::Float64`: 第三ボイラー通過の高圧シャフトパワーの割合、検証範囲: `(0, 0.35)`
  * `K6::Float64`: 第三ボイラー通過の低圧シャフトパワーの割合、検証範囲: `(0, 0.55)`
  * `T7::Float64`: 第四ボイラー通過の時間定数、検証範囲: `(0, 10)`
  * `K7::Float64`: 第四ボイラー通過の高圧シャフトパワーの割合、検証範囲: `(0, 0.3)`
  * `K8::Float64`: 第四ボイラー通過の低圧シャフトパワーの割合、検証範囲: `(0, 0.3)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照パワーセットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) IEEETurbineGovモデルの[状態](@ref S)は次の通りです:

```
x_g1: 最初のガバーレインテグレーター、
x_g2: ガバーレ出力、
x_g3: 最初のタービンインテグレーター、 
x_g4: 第二タービンインテグレーター、 
x_g5: 第三タービンインテグレーター、 
x_g6: 第四タービンインテグレーター、
```

  * `n_states::Int`: (**変更しないでください。**) IEEEG1は6つの状態を持っています
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) IEEEG1は6つの[微分](@ref states_list) [状態](@ref S)を持っています
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
