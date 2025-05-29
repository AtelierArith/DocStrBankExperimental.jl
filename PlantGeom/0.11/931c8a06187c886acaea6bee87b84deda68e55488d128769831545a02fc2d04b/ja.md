```
get_color(var <: AbstractArray, range_var, colormap=colorschemes[:viridis])
get_color(var, range_var, colormap=colorschemes[:viridis])
```

値を範囲に基づいてカラーマップから色にマッピングします

# 引数

  * `var`: 色にマッピングする値
  * `range_var`: 色にマッピングする値の範囲
  * `colormap`: 使用するカラーマップ

# 戻り値

  * `color`: `var` に対応する色

# 例

```julia using Colors

get*color(1, 1:2, colormap = colorschemes[:viridis]) # returns RGB{N0f8}(0.267004,0.00487433,0.329415) get*color(1:2, 1:10, colormap = colorschemes[:viridis]) # returns RGB{N0f8}(0.267004,0.00487433,0.329415) get_color(1:2, 1:10, 1, colormap = colorschemes[:viridis]) # returns RGB{N0f8}(0.267004,0.00487433,0.329415)
```
