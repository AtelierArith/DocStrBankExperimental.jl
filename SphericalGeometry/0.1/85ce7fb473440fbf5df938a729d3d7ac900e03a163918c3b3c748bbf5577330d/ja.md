```
angular_distance(point₃::Point, point₁::Point, point₂::Point)
```

点₃ [deg] から点₁ [deg] で始まり点₂ [deg] で終わる大円の線分上の最も近い点までの `angular_distance` [deg] を返します。大円の線分は単位球面を周回しません。

`angular_distance` は弧の左側または右側にあるときに符号を変えません。
