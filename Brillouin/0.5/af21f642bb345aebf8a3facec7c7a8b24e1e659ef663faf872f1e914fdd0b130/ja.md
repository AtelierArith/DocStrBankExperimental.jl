```
basis(x::Union{KPath, KPathInterpolant, Cell})
```

`x`に関連付けられた（逆または直接の）格子基底を直交座標系で返します。

Brillouinのメソッドはデフォルトで格子基底の点を返します。つまり、点は`basis(x)`に言及されます。これは`setting(x) == LATTICE`に対応します。座標は、[`cartesianize`](@ref)を使用することで、`setting(x) == CARTESIAN`に対応する直交基底に言及される場合があります。しかし、`basis(x)`の結果はこれに対して不変であり、常に直交座標系での格子基底を指します。
