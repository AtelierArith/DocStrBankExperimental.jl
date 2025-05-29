```
valuation(a::AbsSimpleNumFieldElem, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> ZZRingElem
valuation(a::AbsSimpleNumFieldOrderElem, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> ZZRingElem
valuation(a::ZZRingElem, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> ZZRingElem
```

$$
a
$$

の$\mathfrak p$-adic valuationを計算します。つまり、$a$が$\mathfrak p^i$に含まれる最大の$i$を求めます。
