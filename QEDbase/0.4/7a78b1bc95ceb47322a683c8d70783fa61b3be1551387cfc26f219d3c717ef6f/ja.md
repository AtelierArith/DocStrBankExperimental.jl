```
getTransverseMass(lv)
```

与えられた `LorentzVectorLike` の横運動量を返します。すなわち、その平方横質量の平方根です。

!!! example
    `(E,px,py,pz)` が `LorentzVectorLike` の場合、これは `sqrt(E^2 - pz^2)` に相当します。


!!! note
    横成分は3軸に対して定義されています。


!!! note
    もし平方横質量 `mT2` が負であれば、`-sqrt(-mT2)` が返されます。

