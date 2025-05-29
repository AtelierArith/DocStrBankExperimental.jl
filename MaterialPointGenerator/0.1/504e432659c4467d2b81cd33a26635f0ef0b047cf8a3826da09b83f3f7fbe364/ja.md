```
dem2particle(dem, h, bottom)
```

## 説明:

与えられたDEMファイルから粒子を生成します。`dem`は3列（x, y, z）の座標配列です。`h`はz方向の粒子の間隔で、通常はMPMシミュレーションのグリッドサイズと等しいです。`bottom`は値で、平面`z = bottom`を意味します。
