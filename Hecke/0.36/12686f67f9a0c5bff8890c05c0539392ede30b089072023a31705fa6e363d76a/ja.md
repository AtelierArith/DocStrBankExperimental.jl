```
invariants(M::QuadSpace)
      -> FieldElem, Dict{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}, Vector{Tuple{InfPlc, Int}}
```

`M`の不変量のタプル`(n, k, d, H, I)`を返します。これにより、同型類が完全に決定されます。ここで、`n`は次元です。カーネルの次元は`k`です。要素`d`は非退化部分のグラム行列の行列式であり、`H`は非自明なハッセ不変量を含み、`I`は各実数場所の慣性の負のインデックスを含みます。

`d`は平方数の剰余のみで決定されることに注意してください。 ```
