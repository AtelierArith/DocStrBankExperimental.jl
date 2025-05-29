```
getRapidity(lv)
```

与えられた `LorentzVectorLike` の [ラピディティ](https://en.wikipedia.org/wiki/Rapidity) を返します。

!!! example
    `(E,px,py,pz)` が `LorentzVectorLike` の場合、これは `0.5*log((E+pz)/(E-pz))` と同等です。


!!! note
    横成分は 3 軸に対して定義されています。

