```
mutable struct CSVGN1 <: DynamicInjection
    name::String
    K::Float64
    T1::Float64
    T2::Float64
    T3::Float64
    T4::Float64
    T5::Float64
    Rmin::Float64
    Vmax::Float64
    Vmin::Float64
    CBase::Float64
    base_power::Float64
    ext::Dict{String, Any}
    R_th::Float64
    X_th::Float64
    states::Vector{Symbol}
    n_states::Int
    internal::InfrastructureSystemsInternal
end
```

静的シャント補償器のパラメータ: CSVGN1 in PSSE

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例: `PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `K::Float64`: puでのゲイン ([`DEVICE_BASE`](@ref per_unit))、検証範囲: `(0, nothing)`
  * `T1::Float64`: 時間定数（秒）、検証範囲: `(0, nothing)`
  * `T2::Float64`: 時間定数（秒）、検証範囲: `(0, nothing)`
  * `T3::Float64`: 時間定数（秒）、検証範囲: `(eps(), nothing)`
  * `T4::Float64`: 時間定数（秒）、検証範囲: `(0, nothing)`
  * `T5::Float64`: 時間定数（秒）、検証範囲: `(0, nothing)`
  * `Rmin::Float64`: リアクタの最小Mvar、検証範囲: `(0, nothing)`
  * `Vmax::Float64`: 最大電圧（pu）、検証範囲: `(0, nothing)`
  * `Vmin::Float64`: 最小電圧（pu）、検証範囲: `(0, nothing)`
  * `CBase::Float64`: コンデンサ（MVAR）、検証範囲: `(0, nothing)`
  * `base_power::Float64`: ユニットの基準電力（MVA）[per unitization](@ref per_unit)のため、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: (デフォルト: `Dict{String, Any}()`) シミュレーションで使用されないメタデータ（緯度や経度など）を追加するための[*ext*ra辞書](@ref additional_fields)。
  * `R_th::Float64`: ソースのテブナン抵抗
  * `X_th::Float64`: ソースのテブナンリアクタンス
  * `states::Vector{Symbol}`: (**変更しないでください。**) [状態](@ref S)は次のとおりです:

```
thy: サイリスタ,
vr1: レギュレータ出力1,
vr2: レギュレータ出力2
```

  * `n_states::Int`: (**変更しないでください。**) CSVGN1は3つの状態を持ちます
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl内部参照
