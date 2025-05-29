```
pix_to_world(wcs, pixcoords)
```

配列のピクセル座標 `pixcoords` を WCSTransform `wcs` に従って世界座標に変換します。`pixcoords` は 2 次元配列であり、「pixcoords[:, i]」は i 番目の座標セット、または単一の座標セットを表す 1 次元配列である必要があります。

返り値は `pixcoords` と同じ形状です。
