```
mutable struct ReserveDemandCurve{T <: ReserveDirection} <: Reserve{T}
    variable::Union{Nothing, TimeSeriesKey, CostCurve{PiecewiseIncrementalCurve}}
    name::String
    available::Bool
    time_frame::Float64
    sustained_time::Float64
    max_participation_factor::Float64
    deployed_fraction::Float64
    ext::Dict{String, Any}
    internal::InfrastructureSystemsInternal
end
```

運用シミュレーションのための[運用予備需要曲線 (ORDC)](https://hepg.hks.harvard.edu/files/hepg/files/ordcupdate-final.pdf)を持つ予備製品。

ORDCは、時間とともに変化する可能性のある`(予備容量 (MW), 価格 ($/MWh))`のステップの離散化されたセットとしてモデル化されています。ORDCを定義するには、[`set_variable_cost!`](@ref)を使用します。

予備を定義する際には、`ReserveDirection`を指定して、これを[`ReserveUp`](@ref)、[`ReserveDown`](@ref)、または[`ReserveSymmetric`](@ref)として定義する必要があります。

# 引数

  * `variable::Union{Nothing, TimeSeriesKey, CostCurve{PiecewiseIncrementalCurve}}`: `variable` = `nothing`でこのオブジェクトを作成し、その後、[`set_variable_cost!`](@ref)関数を使用してコスト曲線または`variable_cost`の時間系列を追加して、このパラメータを自動的に更新します
  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）は一意の名前を持つ必要がありますが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンであるか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます
  * `time_frame::Float64`: 予備貢献を提供するための飽和時間フレーム（分単位）、検証範囲: `(0, nothing)`
  * `sustained_time::Float64`: （デフォルト: `3600.0`）指定されたレベルで予備貢献を維持しなければならない時間（秒単位）、検証範囲: `(0, nothing)`
  * `max_participation_factor::Float64`: （デフォルト: `1.0`）デバイスごとに貢献できる予備の最大部分[0, 1.0]、検証範囲: `(0, 1)`
  * `deployed_fraction::Float64`: （デフォルト: `0.0`）実際に展開されると想定されるサービス調達の割合。一般的には、これは0.0または1.0と想定されます、検証範囲: `(0, 1)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
