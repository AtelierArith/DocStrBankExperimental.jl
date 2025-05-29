```
primary_decomposition(I::AlgAssAbsOrdIdl [O::Order]) -> Vector{Tuple}
```

$$
I
$$

の主成分分解を、$O$に対して、$P$が素で$Q$が$P$-主であるタプル$(P, Q)$のリストとして返します。$I$は$Q$の積です。

$$
O
$$

の有理スパンはエタールでなければならず、順序が指定されていない場合は、$I$の左順序が使用されます。
