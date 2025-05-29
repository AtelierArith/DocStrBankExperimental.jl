```
mutable struct TransmissionInterface <: Service
    name::String
    available::Bool
    active_power_flow_limits::MinMax
    violation_penalty::Float64
    direction_mapping::Dict{String, Int}
    internal::InfrastructureSystemsInternal
end
```

異なる [`Areas`](@ref Area) または [`LoadZones`](@ref LoadZone) の間での電力転送のためのインターフェースまたは回廊を構成するブランチのコレクション。

インターフェースは、その上での電力フローを制約するために使用できます。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例: `PowerLoad`）はユニークな名前を持たなければなりませんが、異なるタイプのコンポーネント（例: `PowerLoad` と `ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow_limits::MinMax`: インターフェース上の最小および最大のアクティブ電力フロー制限（MW）。
  * `violation_penalty::Float64`: （デフォルト: `INFINITE_COST`）インターフェースのフロー制限を違反した場合のペナルティコスト。
  * `direction_mapping::Dict{String, Int}`: （デフォルト: `Dict{String, Int}()`）インターフェース内のライン `name` とそのフローの方向（インターフェースのフローに対して1または-1）を示す辞書。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl の内部参照。
