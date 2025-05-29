```
poverorder(O::AbsSimpleNumFieldOrder, p::ZZRingElem) -> AbsSimpleNumFieldOrder
poverorder(O::AbsSimpleNumFieldOrder, p::Integer) -> AbsSimpleNumFieldOrder
```

この関数は、素数 $p$ において $\mathcal O$ よりも局所的に大きい順序を見つけようとします：もし $p$ が指標 $[ \mathcal O_K : \mathcal O]$ を割り切る場合、この関数は $v_p([ \mathcal O_K : R]) < v_p([ \mathcal O_K : \mathcal O])$ となる順序 $R$ を返します。そうでなければ、$\mathcal O$ が返されます。
