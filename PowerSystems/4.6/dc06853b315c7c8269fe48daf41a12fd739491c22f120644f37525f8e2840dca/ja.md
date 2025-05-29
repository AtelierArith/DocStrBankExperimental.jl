```
mutable struct TGTypeII <: TurbineGov
    R::Float64
    T1::Float64
    T2::Float64
    τ_limits::MinMax
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

タービンガバナータイプIIのパラメータ

# 引数

  * `R::Float64`: ドループパラメータ、検証範囲: `(0, nothing)`
  * `T1::Float64`: 過渡ゲイン時間定数、検証範囲: `(0, nothing)`
  * `T2::Float64`: 電力分数時間定数、検証範囲: `(0, nothing)`
  * `τ_limits::MinMax`: ガバナーへの電力制限
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) TGTypeIモデルの[状態](@ref S)は次のとおりです:

```
x_g1: リードラグ状態
```

  * `n_states::Int`: (**変更しないでください。**) TGTypeIIは1つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
