```
getMinus(lv)
```

与えられた `LorentzVectorLike` のマイナス成分を [光円筒座標](https://en.wikipedia.org/wiki/Light-cone_coordinates) で返します。

!!! example
    `(E,px,py,pz)` が `LorentzVectorLike` の場合、これは `(E-pz)/2` に相当します。


!!! note
    [光円筒座標](https://en.wikipedia.org/wiki/Light-cone_coordinates) は 3 軸に対して定義されています。


!!! warning
    定義 ``p^- := (E - p_z)/2` は、一般相対性理論における [光円筒座標](https://en.wikipedia.org/wiki/Light-cone_coordinates) の通常の定義とは異なります。

