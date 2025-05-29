```
isdegenerate(x::AbstractSimplex, k0::Integer, k1::Integer) -> Bool
```

`x`が区間`k0:k1`で退化している場合は`true`を返し、そうでない場合は`false`を返します。インデックスは`0 <= k0 <= k1 <= dim(x)`を満たす必要があります。

単体は、`k0`と`k1-1`の間のある位置`k`で退化している場合、区間`k0:k1`で退化しています。
