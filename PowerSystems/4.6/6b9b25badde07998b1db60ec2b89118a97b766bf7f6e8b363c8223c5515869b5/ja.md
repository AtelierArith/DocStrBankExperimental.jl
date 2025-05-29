```
mutable struct TGSimple <: TurbineGov
    d_t::Float64
    Tm::Float64
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

シンプルな1状態タービンガバナーのパラメータ

# 引数

  * `d_t::Float64`: 逆ドロップパラメータ、検証範囲: `(0, nothing)`
  * `Tm::Float64`: タービンガバナーのローパス時間定数 [s]、検証範囲: `(0, nothing)`
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) TGSimpleモデルの[状態](@ref S)は：

```
τm: 機械的トルク
```

  * `n_states::Int`: (**変更しないでください。**) TGSimpleは1つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
