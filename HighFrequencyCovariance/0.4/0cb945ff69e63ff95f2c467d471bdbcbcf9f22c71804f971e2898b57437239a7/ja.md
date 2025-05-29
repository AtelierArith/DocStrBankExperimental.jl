```
simple_volatility(
   ts::SortedDataFrame,
   assets::Vector{Symbol} = get_assets(ts);
   time_grid::Union{Missing,Dict} = missing,
   fixed_spacing::Union{Missing,Dict,<:Real} = missing,
   use_all_obs::Bool = false,
   rough_guess_number_of_intervals::Integer = 5,
)
```

単純な方法でボラティリティを計算します。

### 入力

  * `ts` - ティックデータ。
  * `assets` - ボラティリティを推定したい資産。
  * `time_grid` - リターンを計算するためのグリッド。欠損している場合は、固定間隔（提供されている場合）またはデフォルトの間隔で生成されます。
  * `fixed_spacing` - 時間グリッドを計算するために使用される間隔。`time_grid`が入力されている場合や`use_all_obs = true`の場合は使用されません。
  * `use_all_obs` - ボラティリティを推定するためにすべての観測値を使用します。`time_grid`が提供されている場合は使用されません。
  * `rough_guess_number_of_intervals` - デフォルトの間隔を計算するための大まかな間隔の数。`time_grid`または`fixed_spacing`が提供されている場合や`use_all_obs = true`の場合は使用されません。

### 戻り値

  * 各資産の推定ボラティリティを含む`Dict`。
