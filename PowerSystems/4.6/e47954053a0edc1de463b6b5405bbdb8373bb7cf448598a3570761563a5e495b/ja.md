```
mutable struct TGTypeI <: TurbineGov
    R::Float64
    Ts::Float64
    Tc::Float64
    T3::Float64
    T4::Float64
    T5::Float64
    valve_position_limits::MinMax
    P_ref::Float64
    ext::Dict{String, Any}
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

タービンガバナータイプIのパラメータ

# 引数

  * `R::Float64`: ドロップパラメータ、検証範囲: `(0, nothing)`
  * `Ts::Float64`: ガバナー時間定数、検証範囲: `(0, nothing)`
  * `Tc::Float64`: サーボ時間定数、検証範囲: `(0, nothing)`
  * `T3::Float64`: 過渡ゲイン時間定数、検証範囲: `(0, nothing)`
  * `T4::Float64`: 電力分数時間定数、検証範囲: `(0, nothing)`
  * `T5::Float64`: 再加熱時間定数、検証範囲: `(0, nothing)`
  * `valve_position_limits::MinMax`: MW単位のバルブ位置制限
  * `P_ref::Float64`: (デフォルト: `1.0`) 参照電力セットポイント (pu)、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) ユーザーがシミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度。
  * `states::Vector{Symbol}`: (**変更しないでください。**) TGTypeIモデルの[状態](@ref S)は次のとおりです:

```
x_g1: ガバナーステート,
x_g2: サーボステート,
x_g3: 再加熱ステート
```

  * `n_states::Int`: (**変更しないでください。**) TGTypeIは3つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
