目的の時系列データセットにアクセスするために使用できるキーのスーパタイプ

具体的なサブタイプ:

  * [`StaticTimeSeriesKey`](@ref)
  * [`ForecastKey`](@ref)

必要なメソッド:

  * `get_name`
  * `get_resolution`
  * `get_time_series_type`

デフォルトのメソッドは、フィールド名 `name` と `time_series_type` に依存しています。
