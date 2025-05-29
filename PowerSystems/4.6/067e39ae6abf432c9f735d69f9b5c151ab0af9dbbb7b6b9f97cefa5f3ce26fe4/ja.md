```
mutable struct VariableReserveNonSpinning <: ReserveNonSpinning
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

時間変動する調達要件を持つ非回転予備製品、例えば、予想される高負荷や高ランプの時間帯における高い要件など。

この予備製品には、現在電力システムと同期していない可能性のあるバックアップ発電機が含まれていますが、送電線や発電機の停止などの予期しない事態の後に迅速にオンラインになることができます。時間変動する要件をモデル化するために、この予備に["`requirement`"の時系列を追加する必要があります](@ref ts_data)。

これは上向きの予備のみです。システムとすでに同期しているコンポーネントからのより迅速に応答する上向きまたは下向きの予備については、[`VariableReserve`](@ref)を参照してください。

# 引数

  * `name::String`: コンポーネントの名前。同じタイプのコンポーネント（例：`PowerLoad`）はユニークな名前を持たなければなりませんが、異なるタイプのコンポーネント（例：`PowerLoad`と`ACBus`）は同じ名前を持つことができます。
  * `available::Bool`: コンポーネントが接続されてオンラインであるか（`true`）、切断されてオフラインまたはダウンしているか（`false`）を示す指標。利用できないコンポーネントはシミュレーション中に除外されます。
  * `time_frame::Float64`: 予備貢献を提供するための飽和時間枠（分単位）、検証範囲: `(0, nothing)`
  * `requirement::Float64`: 製品の必要な数量はTimeSeriesDataによってスケーリングされるべきです。
  * `sustained_time::Float64`: （デフォルト: `14400.0`）指定されたレベルで予備貢献を維持しなければならない時間（秒単位）、検証範囲: `(0, nothing)`
  * `max_output_fraction::Float64`: （デフォルト: `1.0`）サービスに割り当てることができる各デバイスの出力の最大割合、検証範囲: `(0, 1)`
  * `max_participation_factor::Float64`: （デフォルト: `1.0`）デバイスごとに貢献できる予備の最大部分[0, 1.0]、検証範囲: `(0, 1)`
  * `deployed_fraction::Float64`: （デフォルト: `0.0`）実際に展開されると想定されるサービス調達の割合。一般的には、これは0.0または1.0と想定されます、検証範囲: `(0, 1)`
  * `ext::Dict{String, Any}`: （デフォルト: `Dict{String, Any}()`）シミュレーションで使用されないメタデータを追加するための[*ext*ra辞書](@ref additional_fields)、例えば緯度と経度など。
  * `internal::InfrastructureSystemsInternal`: （**変更しないでください。**）PowerSystems.jl内部参照
