```
DeviceModel(
    ::Type{D},
    ::Type{B},
    feedforwards::Vector{<:AbstractAffectFeedforward}
    use_slacks::Bool,
    duals::Vector{DataType},
    services::Vector{ServiceModel}
    attributes::Dict{String, Any}
)
```

特定のデバイスのモデルをタイプによって確立します。キーワード引数feedforwardを使用して、シミュレーション時に操作モデル間で値を渡すことを可能にします。

# 引数

  * `::Type{D} where D<:PSY.Device`: 電力システムデバイスタイプ
  * `::Type{B} where B<:AbstractDeviceFormulation`: 抽象デバイス定式化
  * `feedforward::Array{<:AbstractAffectFeedforward} = Vector{AbstractAffectFeedforward}()` : モデル間でパラメータを渡すために使用
  * `use_slacks::Bool = false` : デバイスモデルにスラックを追加します。実装はモデル依存であり、すべてのモデルがスラックを特徴としているわけではありません
  * `duals::Vector{DataType} = Vector{DataType}()`: デュアルを計算するために制約タイプを渡すために使用します。DataTypeは有効なConstraintTypeである必要があります
  * `time_series_names::Dict{Type{<:TimeSeriesParameter}, String} = get_default_time_series_names(D, B)` : デバイスに関連付けられた時系列名を指定するために使用
  * `attributes::Dict{String, Any} = get_default_attributes(D, B)` : デバイスに属性を指定するために使用

# 例

```julia
thermal_gens = DeviceModel(ThermalStandard, ThermalBasicUnitCommitment)
```
