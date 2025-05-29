```
lift(a::TorQuadModuleElem) -> Vector{QQFieldElem}
```

`a`を`cover(parent(a))`の周囲空間に持ち上げます。

$$
a + N \in M/N
$$

の場合、これは代表元$a$を返します。
