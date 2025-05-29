```
pmaximal_overorder(O::AbsSimpleNumFieldOrder, p::ZZRingElem) -> AbsSimpleNumFieldOrder
pmaximal_overorder(O::AbsSimpleNumFieldOrder, p::Integer) -> AbsSimpleNumFieldOrder
```

この関数は、$\mathcal O$を含む$p$-最大整域$R$を見つけます。すなわち、指標$[ \mathcal O_K : R]$は$p$で割り切れません。
