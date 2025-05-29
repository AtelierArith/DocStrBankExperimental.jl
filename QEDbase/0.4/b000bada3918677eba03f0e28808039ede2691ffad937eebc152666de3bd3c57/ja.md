```
getMagnitude(lv)
```

与えられた `LorentzVectorLike` の大きさ、すなわちユークリッドノルムの空間成分を返します。

!!! example
    `(t,x,y,z)` が `LorentzVectorLike` の場合、これは `sqrt(x^2 + y^2 + z^2)` に相当します。


!!! warning
    この関数は、有名な `ROOT` ライブラリで使用される `TLorentzVector` の類似関数とは異なります。

