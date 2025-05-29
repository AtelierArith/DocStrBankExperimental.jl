```
neighbors(x::Union{Neighborhood,NeighborhoodRule}}) -> iterable
```

近傍内のすべてのセルに対するインデックス可能なイテレータを返します。値の `Tuple` または範囲のいずれかです。

カスタム `Neighborhood` はこのメソッドを定義する必要があります。
