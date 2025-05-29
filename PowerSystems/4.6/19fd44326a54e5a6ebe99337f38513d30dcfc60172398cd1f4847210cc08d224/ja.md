```
mutable struct AreaInterchange <: Branch
    name::String
    available::Bool
    active_power_flow::Float64
    from_area::Area
    to_area::Area
    flow_limits::FromTo_ToFrom
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

エリア間で交換されるフロー。このインターチェンジは、エリアを接続するラインには依存しません。これは、ラインのグループ全体を通じた総フローであるインターフェースの代わりにはなりません。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示すインジケーター。利用できないコンポーネントはシミュレーション中に除外されます。
  * `active_power_flow::Float64`: ライン上のアクティブパワーフローの初期条件（MW）。
  * `from_area::Area`: 電力が抽出されるエリア。
  * `to_area::Area`: 電力が注入されるエリア。
  * `flow_limits::FromTo_ToFrom`: エリア間の最大フロー。ラインや他のブランチの合計は無視されます。
  * `ext::Dict{String, Any}`: （デフォルト：`Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度や経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jlの内部参照。
