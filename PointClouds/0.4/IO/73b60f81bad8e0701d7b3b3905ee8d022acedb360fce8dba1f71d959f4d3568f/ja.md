```
color_channels(Integer, p::PointRecord)
color_channels(Integer, points, inds = :)
```

各色チャネルに関連付けられた「生」の強度を符号なし16ビット整数のタプルとして取得します。PDRF 2、3、5、および7の場合、これは赤、緑、青チャネルに対応する3つの値を返しますが、PDRF 8および10には近赤外チャネルのための4番目の値が含まれています。値は0から65535の範囲をカバーするように正規化されるべきです。色情報を含まないPDRFの場合は`missing`が返されます。

参照: [`PointRecord`](@ref), [`intensity`](@ref)
