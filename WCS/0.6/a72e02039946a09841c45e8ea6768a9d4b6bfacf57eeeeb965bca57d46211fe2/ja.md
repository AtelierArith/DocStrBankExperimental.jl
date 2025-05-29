```
world_to_pix!(wcs, worldcoords, pixcoords[; stat=, phi=, theta=, imcoords=])
```

配列のピクセル座標 `worldcoords` を WCSTransform `wcs` に従ってピクセル座標に変換し、その結果を `pixcoords` 配列に格納します。`worldcoords` は 2 次元配列であり、「worldcoords[:, i]」は i 番目の座標セット、または単一の座標セットを表す 1 次元配列である必要があります。`pixcoords` は `worldcoords` と同じサイズと型でなければなりません。

与えられた場合、配列 `stat`、`imcoords`、`phi`、`theta` は中間結果を格納するために使用されます。それらのサイズと型はすべて `worldcoords` と一致する必要がありますが、`stat` は同じサイズである必要がありますが、型は Cint（通常は Int32）である必要があります。
