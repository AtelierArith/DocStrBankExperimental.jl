```
geocentric_to_ecef(lat::Number, lon::Number, r::Number) -> SVector{3, T}
```

地心座標（緯度 `lat` [rad]、経度 `lon` [rad]、および地球の中心からの距離 `r` [m]）を地球中心・地球固定ベクトル [m] に変換します。

!!! note
    出力型 `T` は、入力型 `T1`、`T2`、および `T3` を昇格させることによって得られます。すべてが整数の場合、それらは浮動小数点に変換されます。

