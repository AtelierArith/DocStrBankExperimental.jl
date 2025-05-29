```
mutable struct STAB1 <: PSS
    KT::Float64
    T::Float64
    T1T3::Float64
    T3::Float64
    T2T4::Float64
    T4::Float64
    H_lim::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    states_types::Vector{StateTypes}
    internal::InfrastructureSystemsInternal
end
```

スピード感度安定化モデル

# 引数

  * `KT::Float64`: 洗い出しフィルタのK/T、検証範囲: `(0, nothing)`
  * `T::Float64`: 洗い出しフィルタの時間定数、検証範囲: `(0.01, nothing)`
  * `T1T3::Float64`: 時間定数の比 T1/T3、検証範囲: `(0, nothing)`
  * `T3::Float64`: 時間定数、検証範囲: `(0.01, nothing)`
  * `T2T4::Float64`: 時間定数の比 T2/T4、検証範囲: `(0, nothing)`
  * `T4::Float64`: 時間定数、検証範囲: `(0.01, nothing)`
  * `H_lim::Float64`: PSS出力制限、検証範囲: `(0, 0.5)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は：

```
x_p1: 洗い出しフィルタ,
x_p2: T1/T3 リードラグブロック, 
x_p3: T2/T4 リードラグブロック,
```

  * `n_states::Int`: (**変更しないでください。**) STAB1は3つの状態を持つ
  * `states_types::Vector{StateTypes}`: (**変更しないでください。**) STAB1は3つの[differential](@ref states_list) [状態](@ref S)を持つ
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
