```
ref(A::Union{ArbMatrixOrRef,AcbMatrixOrRef}, i, j)
```

`A[i,j]`と似ていますが、`Arb`または`Acb`の代わりに`ArbRef`または`AcbRef`を返し、`A`の`(i,j)`-thエントリとメモリを共有します。
