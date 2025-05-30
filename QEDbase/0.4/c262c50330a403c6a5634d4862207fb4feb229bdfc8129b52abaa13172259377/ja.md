```
getPlus(lv)
```

与えられた `LorentzVectorLike` のプラス成分を [光円筒座標](https://en.wikipedia.org/wiki/Light-cone_coordinates) で返します。

!!! example
    `(E,px,py,pz)` が `LorentzVectorLike` の場合、これは `(E+pz)/2` に相当します。


!!! note
    [光円筒座標](https://en.wikipedia.org/wiki/Light-cone_coordinates) は 3 軸に関して定義されています。


!!! warning
    定義 $p^+ := (E + p_z)/2$ は一般相対性理論における通常の [光円筒座標](https://en.wikipedia.org/wiki/Light-cone_coordinates) の定義とは異なります。

