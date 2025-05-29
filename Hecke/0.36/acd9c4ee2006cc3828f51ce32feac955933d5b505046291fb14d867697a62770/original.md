```
is_isomorphic_with_map(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldElem
is_isomorphic_with_map(I::NfFracOrdIdl, J::NfFracOrdIdl) -> Bool, AbsSimpleNumFieldElem
is_isomorphic_with_map(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl) -> Bool, AbstractAssociativeAlgebraElem
```

Given two (fractional) ideals $I$ and $J$ of an order $R$ of an $Q$-étale algebra $A$, this function returns `true` and an element $a \in A$ such that $I = aJ$ if such an element exists and `false` and $0$ otherwise.
