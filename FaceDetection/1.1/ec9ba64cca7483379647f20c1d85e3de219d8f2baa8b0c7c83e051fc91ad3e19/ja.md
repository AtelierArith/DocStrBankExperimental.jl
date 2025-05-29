```
sum_region(
	integral_image_arr::AbstractArray,
	top_left::Tuple{Int,Int},
	bottom_right::Tuple{Int,Int}
) -> Number
```

# 引数

  * `iA::IntegralArray{T, N}`: 中間積分画像
  * `top_left::NTuple{N, Int}`: 矩形の左上隅の座標
  * `bottom_right::NTuple{N, Int}`: 矩形の右下隅の座標

# 戻り値

  * `sum::T` パラメータ `top_left` と `bottom_right` で定義された矩形内のすべてのピクセルの合計
