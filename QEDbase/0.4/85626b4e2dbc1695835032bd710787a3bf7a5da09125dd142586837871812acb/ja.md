```
getPhi(lv)
```

与えられた `LorentzVectorLike` の phi 角を返します。すなわち、[球面座標](https://en.wikipedia.org/wiki/Spherical_coordinate_system)におけるその空間成分の方位角です。

!!! example
    `(E,px,py,pz)` が `LorentzVectorLike` の場合、これは `atan(py,px)` と同等です。


!!! note
    [球面座標](https://en.wikipedia.org/wiki/Spherical_coordinate_system) は 3 軸に対して定義されています。

