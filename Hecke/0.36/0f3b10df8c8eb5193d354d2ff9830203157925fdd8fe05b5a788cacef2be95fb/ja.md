```
primary_decomposition(I::AlgAssAbsOrdIdl [O::Order]) -> Vector{Tuple}
```

$$
I
$$

の主成分分解を順序$O$に対してタプルのリスト$(P, Q)$として返します。ここで、$P$は素であり、$Q$は$P$-主成分であり、$I$は$Q$の積です。

$$
O
$$

の有理スパンはエタールでなければならず、順序が指定されていない場合は、$I$の左順序が使用されます。
