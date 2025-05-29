```
isdegenerate(x::AbstractSimplex, k::Integer) -> Bool
```

`x`が位置`k`で退化している場合は`true`を返し、そうでない場合は`false`を返します。インデックス`k`は`0`と`dim(x)-1`の間でなければなりません。

正の次元の単体`x`は、位置`k`で退化している場合、`x == s(d(x, k), k)`となります。
