```
get_timegrid(
    ts::SortedDataFrame,
    assets::Vector{Symbol},
    time_grid::Missing,
    fixed_spacing::Union{Missing,<:Real},
    refresh_times::Bool,
    rough_guess_number_of_intervals::Integer,
)

get_timegrid(
    ts::SortedDataFrame,
    assets::Vector{Symbol},
    time_grid::Vector,
    fixed_spacing::Union{Missing,<:Real},
    refresh_times::Bool,
    rough_guess_number_of_intervals::Integer,
)
```

これは、SortedDataFrameから価格を照会できる時刻のシーケンスを返します。これは、simple_covarianceメソッドで使用されます。

### 入力

  * `ts` - ティックデータ。
  * `time_grid` - リターンを計算するためのグリッド。
  * `fixed_spacing` - 時間グリッドを計算するために使用される間隔。`refresh_times=true`の場合は使用されません。
  * `refresh_times` - 共分散を推定するために更新された時刻を使用するべきか。
  * `rough_guess_number_of_intervals` - デフォルトの間隔を計算するための大まかな間隔の数。`time_grid`または`fixed_spacing`が提供されている場合、または`refresh_times=true`の場合は使用されません。

### 戻り値

  * `Vector{<:Real}`。
