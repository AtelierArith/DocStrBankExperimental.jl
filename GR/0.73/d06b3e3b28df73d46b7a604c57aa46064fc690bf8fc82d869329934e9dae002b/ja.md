```
contourf(px, py, h, pz, major_h::Int)
```

三次元データセットの塗りつぶし等高線を描画します。値は矩形メッシュ上で指定されます。

**パラメータ:**

`x` :     X座標を含むリスト `y` :     Y座標を含むリスト `h` :     高さ値のZ座標を含むリスト `z` :     長さ `len(x)` * `len(y)` のリストまたは適切な次元の配列で、Z座標を含みます `major_h` :     （将来の使用を意図しています）
