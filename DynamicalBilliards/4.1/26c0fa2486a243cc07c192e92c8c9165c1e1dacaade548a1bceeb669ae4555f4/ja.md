```
from_bcoords(ξ, sφ, o::Obstacle) -> pos, vel
```

障害物上の境界座標 `ξ, sφ` を実座標 `pos, vel` に変換します。

`vel` は常に障害物から離れる方向を指します。

この関数は [`to_bcoords`](@ref) の逆関数です。
