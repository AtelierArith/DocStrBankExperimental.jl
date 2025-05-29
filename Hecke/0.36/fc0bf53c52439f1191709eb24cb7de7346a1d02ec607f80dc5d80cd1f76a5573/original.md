```
quo(O::AbsSimpleNumFieldOrder, I::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> AbsSimpleNumFieldOrderQuoRing, Map
quo(O::AlgAssAbsOrd, I::AlgAssAbsOrdIdl) -> AbsOrdQuoRing, Map
```

The quotient ring $O/I$ as a ring together with the projection $M: O\to O/I$. The pointwise inverse of $M$ implements a preimage/ lift function. In    general this will not be a section as it will not be linear.
