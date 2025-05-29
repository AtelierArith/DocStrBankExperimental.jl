StaticTimeSeriesCacheを構築して、時系列データのキャッシングを自動的に制御します。`cache_size_bytes`に基づいてメモリ内のデータ行を維持します。

Base.iterateまたは[`get_time_series_array`](@ref)を呼び出してデータを取得します。各イテレーションはサイズ1のTimeSeries.TimeArrayを返します。

# 引数

  * `::Type{T}`: StaticTimeSeriesのサブタイプ
  * `component::InfrastructureSystemsComponent`: コンポーネント
  * `name::AbstractString`: 時系列名
  * `cache_size_bytes = TIME_SERIES_CACHE_SIZE_BYTES`: メモリ内に保持するデータの最大サイズ
  * `ignore_scaling_factors = false`: 時系列インスタンスの`scaling_factor_multiplier`を無視するかどうかを制御します
