```
vlines!(ax::Axis, xs; ymin = 0.0, ymax = 1.0, attrs...)
```

`ax`上にデータ座標の`xs`で垂直線を作成し、軸座標の`ymin`から`ymax`（0から1）まで描画します。これらの3つはすべて単一または複数の値を持つことができ、最終的な線分を計算するためにブロードキャストされます。
