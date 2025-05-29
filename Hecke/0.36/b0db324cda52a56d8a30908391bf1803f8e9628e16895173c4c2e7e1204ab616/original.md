```
AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(O::AbsSimpleNumFieldOrder, a::ZZMatrix) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

Creates the ideal of $O$ with basis matrix $a$.
No sanity checks. No data is copied, $a$ should not be used anymore.
```

AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(a::ZZRingElem, b::AbsSimpleNumFieldOrderElem) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

```
Creates the ideal $(a,b)$ of the order of $b$.
No sanity checks. No data is copied, $a$ and $b$ should not be used anymore.
```

AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(O::AbsSimpleNumFieldOrder, a::ZZRingElem, b::AbsSimpleNumFieldElem) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

```
Creates the ideal $(a,b)$ of $O$.
No sanity checks. No data is copied, $a$ and $b$ should not be used anymore.
```

AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}(x::AbsSimpleNumFieldOrderElem) -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}

```
Creates the principal ideal $(x)$ of the order of $O$.
No sanity checks. No data is copied, $x$ should not be used anymore.
```
