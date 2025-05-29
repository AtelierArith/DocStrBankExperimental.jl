```
getMagnitude2(lv)
```

与えられた `LorentzVectorLike` の大きさの二乗、すなわち空間成分の二乗の合計を返します。

!!! example
    `(t,x,y,z)` が `LorentzVectorLike` の場合、これは `x^2+ y^2 + z^2` に相当します。


!!! warning
    この関数は、有名な `ROOT` ライブラリで使用される `TLorentzVector` の類似関数とは異なります。

