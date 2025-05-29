```
is_isomorphic(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldElem
is_isomorphic(I::NfFracOrdIdl, J::NfFracOrdIdl) -> Bool, AbsSimpleNumFieldElem
is_isomorphic(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl) -> Bool, AbstractAssociativeAlgebraElem
```

Given two (fractional) ideals $I$ and $J$ of an order $R$ of an $Q$-étale algebra $A$, this function returns `true` if an element $a \in A$ exists such that $I = aJ$ and `false` otherwise.
