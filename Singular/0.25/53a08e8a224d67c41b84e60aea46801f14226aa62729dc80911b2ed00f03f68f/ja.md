```
divrem(I::sideal{S}, G::sideal{S}; complete_reduction::Bool = false) where S <: SPolyUnion
```

`I`の生成子を`G`の生成子で割った余りを計算します。タプル(Quo, Rem, U)を返し、ここで`Matrix(I)*Matrix(U) = Matrix(G)*Matrix(Quo) + Matrix(Rem)`であり、`Rem = normalform(I, G)`です。`U`は、局所環の順序付けに対してのみ単位行列と異なる対角行列です。
