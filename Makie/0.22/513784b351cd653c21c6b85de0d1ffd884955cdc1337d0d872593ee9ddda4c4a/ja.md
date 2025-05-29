```
SpotLight(color, position, direction, angles)
```

位置`position`から方向`direction`に向かって光の円錐を照らすスポットライトを作成します。開口角は`angles`で与えられた内角と外角によって定義され、その間で光の強度が減少します。

利用可能性:

  * GLMakie `shading = MultiLightShading`を使用
  * RPRMakie
