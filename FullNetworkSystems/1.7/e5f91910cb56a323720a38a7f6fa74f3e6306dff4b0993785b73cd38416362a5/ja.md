```julia
mutable struct SystemDA <: FullNetworkSystems.System
```

デイアヘッド市場をモデル化するための `System` のサブタイプ。

フィールド:

  * `gens_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{Int64}}`: バス名をキーとし、そのバスの発電機IDを値とする `Dictionary`
  * `incs_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: バス名をキーとし、そのバスの増分入札IDを値とする `Dictionary`
  * `decs_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: バス名をキーとし、そのバスの減分入札IDを値とする `Dictionary`
  * `psls_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: バス名をキーとし、そのバスの価格感応負荷入札IDを値とする `Dictionary`
  * `loads_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: バス名をキーとし、そのバスの負荷IDを値とする `Dictionary`
  * `zones::Dictionaries.Dictionary{Int64, FullNetworkSystems.Zone}`: `System` 内のゾーン。市場全体のゾーンのための `Zone` エントリも含まれる
  * `buses::Dictionaries.Dictionary{InlineStrings.String15, FullNetworkSystems.Bus}`: バス名でインデックスされた `System` 内のバス
  * `generators::Dictionaries.Dictionary{Int64, FullNetworkSystems.Generator}`: ユニットコードでインデックスされた `System` 内の発電機
  * `branches::Dictionaries.Dictionary{InlineStrings.String31, FullNetworkSystems.Branch}`: バス名でインデックスされた `System` 内のブランチ
  * `lodfs::Dictionaries.Dictionary{String, AxisKeys.KeyedArray{Float64, 2}}`: `Dictionary` のキーによって与えられる一連の非常事態に対するシステムのラインアウトage分布係数行列。各エントリは `KeyedArray` で、軸キーは `branch names x branch on outage`
  * `ptdf::Union{Missing, AxisKeys.KeyedArray{Float64, 2}}`: システムの電力移転分布係数。 `KeyedArray` で、軸キーは `branch names x bus names`
  * `generator_time_series::FullNetworkSystems.GeneratorTimeSeries`: 発電機関連の時系列データ
  * `generator_status::FullNetworkSystems.GeneratorStatusDA`: デイアヘッドの定式化に必要な発電機の状態時系列
  * `loads::AxisKeys.KeyedArray{Float64, 2}`: 負荷の時系列データ。 `KeyedArray` で、軸キーは `load ids x datetimes`
  * `increments::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: 増分入札の時系列データ。 `KeyedArray` で、軸キーは `bid ids x datetimes`
  * `decrements::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: 減分入札の時系列データ。 `KeyedArray` で、軸キーは `bid ids x datetimes`
  * `price_sensitive_loads::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: 価格感応負荷入札の時系列データ。 `KeyedArray` で、軸キーは `bid ids x datetimes`
