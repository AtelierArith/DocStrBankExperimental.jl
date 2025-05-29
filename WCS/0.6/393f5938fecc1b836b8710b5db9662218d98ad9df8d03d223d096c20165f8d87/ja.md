```
pix_to_world!(wcs, pixcoords, worldcoords[; stat=, imcoords=, phi=, theta=])
```

配列のピクセル座標 `pixcoords` を WCSTransform `wcs` に従って世界座標に変換し、結果を `worldcoords` および `stat` 配列に格納します。`pixcoords` は 2 次元配列であり、「pixcoords[:, i]」は i 番目の座標セット、または単一の座標セットを表す 1 次元配列である必要があります。`worldcoords` は `pixcoords` と同じサイズと型でなければなりません。

与えられた場合、配列 `stat`、`imcoords`、`phi`、`theta` は中間結果を格納するために使用されます。それらのサイズと型はすべて `pixcoords` と一致する必要がありますが、`stat` は同じサイズである必要がありますが、型は Cint（通常は Int32）でなければなりません。
