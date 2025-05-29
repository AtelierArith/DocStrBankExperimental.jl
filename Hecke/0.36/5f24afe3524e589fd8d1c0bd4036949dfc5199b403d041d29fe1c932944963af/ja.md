```
unit_group_fac_elem(O::AbsSimpleNumFieldOrder) -> FinGenAbGroup, Map
```

群 $U$ と同型写像 $f \colon U \to \mathcal O^\times$ を返します。$\mathcal O$ の基本単位の集合は `[ f(U[1+i]) for i in 1:unit_group_rank(O) ]` を介して得られます。`f(U[1])` はトーション部分群の生成元を与えます。すべての要素は因子形式で返されます。
