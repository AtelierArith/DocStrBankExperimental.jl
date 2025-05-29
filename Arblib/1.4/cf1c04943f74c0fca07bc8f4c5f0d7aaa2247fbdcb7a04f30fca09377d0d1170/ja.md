```
ref(v::Union{ArbVectorOrRef,AcbVectorOrRef}, i)
```

`v[i]`と似ていますが、`Arb`または`Acb`の代わりに、`v`の`i`番目のエントリとメモリを共有する`ArbRef`または`AcbRef`を返します。
