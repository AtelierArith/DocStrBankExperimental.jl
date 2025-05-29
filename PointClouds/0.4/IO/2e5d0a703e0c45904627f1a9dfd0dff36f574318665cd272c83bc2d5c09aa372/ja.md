```
color_channels(p::PointRecord)
color_channels(points, inds = :)
```

各色チャネルに関連付けられた強度を、0から1の範囲に正規化された値のタプルとして取得します。PDRF 2、3、5、および7の場合、これは赤、緑、青チャネルに対応する3つの値を返しますが、PDRF 8および10には近赤外チャネルのための4番目の値が含まれています。色情報を含まないPDRFの場合は、`missing`が返されます。

参照: [`PointRecord`](@ref), [`intensity`](@ref)
