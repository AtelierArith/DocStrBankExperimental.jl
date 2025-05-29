```
calc_course(velocityENU, elevation, azimuth, down_wind_direction = π/2, respos=true)
```

コース角をラジアンで計算します。

  * velocityENU:         東北上参照フレームにおける凧の速度
  * down*wind*direction: 風が吹いている方向; 北がゼロ; 上から見て時計回りが正; デフォルト: 東に向かっている。
  * respos:              trueの場合、結果は範囲0 .. 2πに、そうでない場合は-π .. πになります。
