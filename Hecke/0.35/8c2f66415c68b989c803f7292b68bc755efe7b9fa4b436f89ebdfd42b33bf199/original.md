```
valuation(a::AbsSimpleNumFieldElem, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> ZZRingElem
valuation(a::AbsSimpleNumFieldOrderElem, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> ZZRingElem
valuation(a::ZZRingElem, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> ZZRingElem
```

Computes the $\mathfrak p$-adic valuation of $a$, that is, the largest $i$ such that $a$ is contained in $\mathfrak p^i$.
