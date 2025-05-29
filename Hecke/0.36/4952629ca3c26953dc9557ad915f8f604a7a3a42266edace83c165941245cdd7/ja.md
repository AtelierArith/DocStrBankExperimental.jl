```
chain_complex(A::Map{FinGenAbGroup, FinGenAbGroup, <:Any, <:Any}...) -> ComplexOfMorphisms{FinGenAbGroup}
```

写像 $A_i$ が $\Im(A_i) \subseteq \Kern(A_{i+1})$ を満たす場合、これによりチェーン複体が作成されます。
