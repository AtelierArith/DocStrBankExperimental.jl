```
rounded_corner(p0::Point{T}, p1::Point{T}, p2::Point{T}, radius::S;
    atol, min_side_len, min_angle)
```

`p0, p1, p2` で定義されたコーナーを半径 `radius` で丸める円弧の点のベクトル。

## キーワード引数

  * `atol`: 許容誤差は、任意のセグメントから実際の円までの最大距離にほぼ等しい。デフォルトは1.0nm（単位を使用しない場合は0.001）。
  * `min_side_len`: 丸められる最小の辺の長さ（例えば、90度の角度の場合、`min_side_len = 2 * rounding_radius` とするのが理にかなっています）。
  * `min_angle`: 隣接する辺が `min_angle` で設定された許容誤差内で共線の場合、丸めは行われません。
