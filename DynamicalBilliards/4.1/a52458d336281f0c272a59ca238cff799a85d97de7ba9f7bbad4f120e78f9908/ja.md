```
billiard_polygon(n::Int, R, center = [0,0]; setting = "standard")
```

`n`辺、半径`r`、および指定された`center`を持つ正多角形ビリヤードを定義する障害物のベクトルを返します。

注意: `R`は、いわゆる外半径を示し、内半径ではありません。

### 設定

  * "standard" : 衝突時に鏡面反射が発生します。
  * "periodic" : 壁は`PeriodicWall`タイプであり、境界での周期性を強制します。`n=4`または`n=6`の場合のみ利用可能です。
  * "random" : 衝突時に速度がランダム化されます。
