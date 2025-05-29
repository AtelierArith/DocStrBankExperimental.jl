ForecastCacheを構築して、予測データのキャッシングを自動的に制御します。`cache_size_bytes`に基づいて、メモリ内の予測ウィンドウのカウントを維持します。

Base.iterateまたは[`get_next_time_series_array!`](@ref)を呼び出してデータを取得します。各イテレーションは、長さ`horizon_count`の1つの予測ウィンドウをカバーするTimeSeries.TimeArrayを返します。

# 引数

  * `::Type{T}`: Forecastのサブタイプ
  * `component::InfrastructureSystemsComponent`: コンポーネント
  * `name::AbstractString`: 予測名
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 予測開始時間
  * `horizon_count::Union{Nothing, Int} = nothing`: 予測ホライズンカウント
  * `cache_size_bytes = TIME_SERIES_CACHE_SIZE_BYTES`: メモリに保持するデータの最大サイズ
  * `ignore_scaling_factors = false`: タイムシリーズインスタンスの`scaling_factor_multiplier`を無視するかどうかを制御します
