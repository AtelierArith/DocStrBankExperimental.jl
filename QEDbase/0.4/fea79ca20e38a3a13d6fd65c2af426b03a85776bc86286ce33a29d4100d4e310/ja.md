```
getTheta(lv)
```

与えられた `LorentzVectorLike` のためのシータ角を返します。すなわち、[球面座標](https://en.wikipedia.org/wiki/Spherical_coordinate_system)におけるその空間成分の極角です。

!!! example
    `(E,px,py,pz)` が大きさ `rho` の `LorentzVectorLike` である場合、これは `arccos(pz/rho)` に相当し、また `arctan(sqrt(px^2+py^2)/pz)` にも相当します。


!!! note
    [球面座標](https://en.wikipedia.org/wiki/Spherical_coordinate_system)は3軸に対して定義されています。

