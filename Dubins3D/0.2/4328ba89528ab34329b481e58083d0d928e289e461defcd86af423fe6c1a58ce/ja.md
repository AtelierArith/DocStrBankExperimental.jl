```
DubinsManeuver3D 構造体
```

この構造体は、操縦に関するすべての必要な情報を含んでいます。

  * qi - 初期構成 (x, y, z, heading, pitch)
  * qf - 最終構成 (x, y, z, heading, pitch)
  * rhomin - 最小旋回半径
  * pitchlims - ピッチ角の制限 [pitch*min, pitch*max]  ただし pitch_min < 0.0
  * path - 水平および垂直のダビンズパスを含む配列
  * length - 3D操縦の総長さ
