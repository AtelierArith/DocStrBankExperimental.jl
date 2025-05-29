```
billiard_rectangle(x=1.0, y=1.0; setting = "standard")
```

サイズ (`x`, `y`) の長方形ビリヤードを定義する障害物のベクトルを返します。

### 設定

  * "standard" : 衝突時に鏡面反射が発生します。
  * "periodic" : 壁は `PeriodicWall` タイプであり、境界での周期性を強制します。
  * "random" : 衝突時に速度がランダム化されます。
  * "ray-splitting" : ビリヤード内のすべての障害物が光線分割を許可します。
