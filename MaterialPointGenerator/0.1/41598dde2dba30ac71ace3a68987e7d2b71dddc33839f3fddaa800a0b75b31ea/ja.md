```
dem2particle(dem, h, bottom)
```

## 説明:

与えられたDEMファイルとボトムサーフェスファイルから粒子を生成します。`dem`は3列（x, y, z）を持つ座標の配列で、`DEMSurface`構造体で初期化する必要があります。`bottom::DEMSurface`はDEMと同じxおよびy座標を持ち、z値はdemよりも低くなければなりません。`h`はMPMシミュレーションで使用されるz方向のグリッドサイズのスペースです。
