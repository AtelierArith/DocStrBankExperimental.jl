```
filter_trajectories(collapsed_data::AbstractDataFrame, filter_settings::NamedTuple)
```

小さすぎる、または大きすぎる、遅すぎる、または基板にくっついている可能性のあるマイクロボットをフィルタリングします。

`filter_settings` は次のフィールドを持つ `NamedTuple` です：

  * `MIN_VELOCITY` : 最小速度（um/s）
  * `MIN_BOUNDING_RADIUS` : 最小バウンディング半径（um）
  * `MAX_BOUNDING_RADIUS` : 最大バウンディング半径（um）
  * `MIN_DISPLACEMENT` : 最小総変位（um）

# 例

```julia
filter_settings = (
    MIN_VELOCITY = 10.0,  # um / s  
    MIN_BOUNDING_RADIUS = 3.38,  # um
    MAX_BOUNDING_RADIUS = 75,  # µm
    MIN_DISPLACEMENT = 0,  # µm
)

filtered_collapsed_data = filter_trajectories(collapsed_data, filter_settings)
```
