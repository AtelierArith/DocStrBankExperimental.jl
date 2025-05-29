```
getInvariantMass(lv)
```

与えられた `LorentzVectorLike` の不変質量を返します。すなわち、それ自身とのミンコフスキー内積の平方根です。

!!! example
    `(t,x,y,z)` が `LorentzVectorLike` の場合、これは `sqrt(t^2 - (x^2 + y^2 + z^2))` と同等です。


!!! note
    もし二乗不変質量 `m2` が負であれば、`-sqrt(-m2)` が返されます。

