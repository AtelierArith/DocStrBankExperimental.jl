```julia
struct Geometry1D
```

ホールスラスタの放電チャンネルの幾何学を説明します。

# フィールド

  * `channel_length::Float64`: 放電チャンネルの長さ（メートル単位）
  * `inner_radius::Float64`: 放電チャンネルの内半径（メートル単位）
  * `outer_radius::Float64`: 放電チャンネルの外半径（メートル単位）
  * `channel_area::Float64`: `inner_radius` と `outer_radius` から計算された放電チャンネルの断面積
