```
chain_complex(A::Map{FinGenAbGroup, FinGenAbGroup, <:Any, <:Any}...) -> ComplexOfMorphisms{FinGenAbGroup}
```

Given maps $A_i$ s.th. $\Im(A_i) \subseteq \Kern(A_{i+1})$, this creates the chain complex.
