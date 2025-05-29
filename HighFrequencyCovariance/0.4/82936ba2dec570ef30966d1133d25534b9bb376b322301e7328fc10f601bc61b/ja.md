```
estimate_volatility(
    ts::SortedDataFrame,
    assets::Vector{Symbol} = get_assets(ts),
    method::Symbol = :two_scales_volatility;
    time_grid::Union{Missing,Dict} = missing,
    fixed_spacing::Union{Missing,Dict,<:Real} = missing,
    use_all_obs::Bool = false,
    rough_guess_number_of_intervals::Integer = 5,
    num_grids::Real = default_num_grids(ts),
)
```

これは、このパッケージに含まれる2つのボラティリティ推定技術のための便利なラッパーです。

### 一般的な入力

  * `ts` - ティックデータ。
  * `assets` - tsから共分散を推定したい資産。
  * `method` - メソッドは `:simple_volatility`（単純ボラティリティ法）または `:two_scales_volatility`（二重スケールボラティリティ法）です。

#### `:simple_volatility` メソッドでのみ使用される入力。

  * `time_grid` - リターンを計算するためのグリッド。欠損している場合は、固定間隔（提供されている場合）またはデフォルトの間隔で生成されます。
  * `fixed_spacing` - 時間グリッドを計算するために使用される間隔。`time_grid`が入力されている場合や`use_all_obs = true`の場合は使用されません。
  * `use_all_obs` - ボラティリティを推定するためにすべての観測値を使用します。`time_grid`が提供されている場合は使用されません。
  * `rough_guess_number_of_intervals` - デフォルトの間隔を計算するための大まかな間隔の数。`time_grid`または`fixed_spacing`が提供されている場合や`use_all_obs = true`の場合は使用されません。

#### `:two_scales_volatility` メソッドでのみ使用される入力。

  * `num_grids` - 二重スケール推定で使用されるグリッドの数。

### 戻り値

  * 各資産の推定ボラティリティを含む `Dict`。
