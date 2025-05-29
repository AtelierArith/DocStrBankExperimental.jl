```
mutable struct ConstantReserveGroup{T <: ReserveDirection} <: Service
    name::String
    available::Bool
    requirement::Float64
    ext::Dict{String, Any}
    contributing_services::Vector{Service}
    internal::InfrastructureSystemsInternal
end
```

個々の予備が集まったグループによって満たされる予備製品。

グループの予備要件は、個々の予備要件に加えて追加され、グループ内の個々の予備に貢献するデバイスも、全体のグループ予備要件に貢献することができます。例：スピニングと非スピニングの予備のグループで、スピニング予備を提供するオンライン発電機が非スピニング予備要件にも貢献できる場合。

このモデルは、常にシステムの基準電力の3%など、一定の調達要件を持っています。予備を定義する際には、これを[`ReserveUp`](@ref)、[`ReserveDown`](@ref)、または[`ReserveSymmetric`](@ref)として定義するために`ReserveDirection`を指定する必要があります。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `requirement::Float64`: 必要な予備の値（p.u.）（[`SYSTEM_BASE`](@ref per_unit））、検証範囲: `(0, nothing)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `contributing_services::Vector{Service}`: （デフォルト: `Vector{Service}()`）このグループ要件に貢献するサービス。シミュレーションを行う際にこの制約が効果を持つためには、サービスを追加する必要があります[`PowerSimulations.jl`](https://nrel-sienna.github.io/PowerSimulations.jl/latest/)で。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
