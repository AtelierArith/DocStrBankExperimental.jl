```
pmaximal_overorder(O::AbsSimpleNumFieldOrder, p::ZZRingElem) -> AbsSimpleNumFieldOrder
pmaximal_overorder(O::AbsSimpleNumFieldOrder, p::Integer) -> AbsSimpleNumFieldOrder
```

This function finds a $p$-maximal order $R$ containing $\mathcal O$. That is, the index $[ \mathcal O_K : R]$ is not divisible by $p$.
