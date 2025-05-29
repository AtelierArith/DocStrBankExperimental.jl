```
world_to_pix(wcs, worldcoords)
```

配列の世界座標 `worldcoords` を WCSTransform `wcs` に従ってピクセル座標に変換します。`worldcoords` は 2 次元配列であり、「worldcoords[:, i]」は i 番目の座標セット、または単一の座標セットを表す 1 次元配列です。

返り値は `worldcoords` と同じサイズです。
