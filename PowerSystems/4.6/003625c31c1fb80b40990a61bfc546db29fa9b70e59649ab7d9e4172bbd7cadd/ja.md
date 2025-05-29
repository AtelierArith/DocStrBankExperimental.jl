```
mutable struct SEXS <: AVR
    Ta_Tb::Float64
    Tb::Float64
    K::Float64
    Te::Float64
    V_lim::MinMax
    V_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

簡略化された励磁系モデル - SEXS のパラメータ

# 引数

  * `Ta_Tb::Float64`: 先行および遅延時間定数の比率、検証範囲: `(0, nothing)`
  * `Tb::Float64`: 遅延時間定数、検証範囲: `(eps(), nothing)`
  * `K::Float64`: ゲイン、検証範囲: `(0, nothing)`
  * `Te::Float64`: フィールド回路の時間定数（秒）、検証範囲: `(0, nothing)`
  * `V_lim::MinMax`: フィールド電圧の制限
  * `V_ref::Float64`: (デフォルト: `1.0`) 参照電圧設定値（pu）、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は:	Vf: 電圧フィールド、	Vr: 先行-遅延状態
  * `n_states::Int`: (**変更しないでください。**) SEXSは2つの状態を持つ
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) SEXSは2つの[differential](@ref states_list) [状態](@ref S)を持つ
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
