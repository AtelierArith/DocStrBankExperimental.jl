```
dem2particle(dem, h, bottom, layer)
```

## 説明:

与えられたDEMファイルとボトム値（平坦な底面）から粒子を生成します。`dem`は3列（x, y, z）の座標配列であり、`bottom`値はdemよりも低くなければなりません。`h`はMPMシミュレーションで使用されるz方向のグリッドサイズのスペースです。`layer`は3列（x, y, z）の行列のベクトルであり、層の表面を表します。層は上から下に向かってソートされていることに注意してください。
