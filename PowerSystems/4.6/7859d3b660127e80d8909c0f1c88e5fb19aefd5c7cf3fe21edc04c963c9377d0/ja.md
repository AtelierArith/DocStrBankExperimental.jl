```
mutable struct ConstantReserve{T <: ReserveDirection} <: Reserve{T}
    name::String
    available::Bool
    time_frame::Float64
    requirement::Float64
    sustained_time::Float64
    max_output_fraction::Float64
    max_participation_factor::Float64
    deployed_fraction::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

常にシステムの基準電力の3%のような、一定の調達要件を持つ予備製品。

この予備製品には、送電線や発電機の故障などの予期しない事態の後にすぐに応答できるオンライン発電機が含まれています。予備を定義する際には、これを[`ReserveUp`](@ref)、[`ReserveDown`](@ref)、または[`ReserveSymmetric`](@ref)として定義するために`ReserveDirection`を指定する必要があります。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `time_frame::Float64`: 予備の貢献を提供するための飽和時間枠（分単位）、検証範囲: `(0, nothing)`
  * `requirement::Float64`: 必要な予備の値（p.u.）（[`SYSTEM_BASE`](@ref per_unit)）、検証範囲: `(0, nothing)`
  * `sustained_time::Float64`: （デフォルト: `3600.0`）指定されたレベルで予備の貢献を維持しなければならない時間（秒単位）、検証範囲: `(0, nothing)`
  * `max_output_fraction::Float64`: （デフォルト: `1.0`）サービスに割り当てることができる各デバイスの出力の最大割合、検証範囲: `(0, 1)`
  * `max_participation_factor::Float64`: （デフォルト: `1.0`）デバイスごとに貢献できる予備の最大部分[0, 1.0]、検証範囲: `(0, 1)`
  * `deployed_fraction::Float64`: （デフォルト: `0.0`）実際に展開されると想定されるサービス調達の割合。一般的には、これは0.0または1.0と想定されます、検証範囲: `(0, 1)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
