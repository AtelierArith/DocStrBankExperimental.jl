```
mask(point::Point, focus::Point, width, height)
    max = 1.0,
    min = 0.0,
    easingfunction = easingflat)
```

`focus`、`width`、および `height` によって定義された矩形領域に対して、`point` に関連する 0 と 1 の間の値を計算します。この値は中心で `max` (1.0) に近づき、端で `min` (0.0) に近づきます。
