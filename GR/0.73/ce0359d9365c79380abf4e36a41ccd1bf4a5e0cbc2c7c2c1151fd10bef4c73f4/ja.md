```
cellarray(xmin::Real, xmax::Real, ymin::Real, ymax::Real, dimx::Int, dimy::Int, color)
```

デバイスに依存しない方法でラスタライクな画像を表示します。セル配列関数は、2つのコーナーポイントで与えられた長方形をDIMX X DIMYのセルに分割し、それぞれのセルは与えられたセル配列の対応する色インデックスによって個別に色付けされます。

**パラメータ:**

`xmin`, `ymin` :     長方形の左下の点 `xmax`, `ymax` :     長方形の右上の点 `dimx`, `dimy` :     色インデックス配列のXおよびYの次元 `color` :     色インデックス配列

`xmin`, `xmax`, `ymin` および `ymax` の値はワールド座標で表されます。
