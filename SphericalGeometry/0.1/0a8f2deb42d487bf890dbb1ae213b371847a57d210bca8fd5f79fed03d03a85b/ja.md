```
angular_distance(point₃::Point, points::Vector{Points{T}}) where T<:Float64
```

点point₃ [deg] から弧の集合を表す点の集合の最も近い点までの `angular_distance` [deg] を返します。

`angular_distance` は、弧の左側または右側にいるときに符号を変えません。
