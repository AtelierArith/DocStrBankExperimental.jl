```
divrem(I::smodule{S}, G::smodule{S}; complete_reduction::Bool = false) where S <: SPolyUnion
```

`I`の生成子を`G`の生成子で割った余りを計算します。戻り値はタプル (Quo, Rem, U) であり、`Matrix(I)*Matrix(U) = Matrix(G)*Matrix(Quo) + Matrix(Rem)` かつ `Rem = normalform(I, G)` です。`U` は単位の対角行列で、局所環の順序付けに対してのみ単位行列と異なります。
