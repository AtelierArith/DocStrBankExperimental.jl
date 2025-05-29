```
is_isomorphic_with_map(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldElem
is_isomorphic_with_map(I::NfFracOrdIdl, J::NfFracOrdIdl) -> Bool, AbsSimpleNumFieldElem
is_isomorphic_with_map(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl) -> Bool, AbstractAssociativeAlgebraElem
```

与えられた二つの（分数）理想 $I$ と $J$ は、$Q$-étale 代数 $A$ のオーダー $R$ のものであり、この関数は `true` と $I = aJ$ となるような要素 $a \in A$ を返します（そのような要素が存在する場合）。そうでない場合は `false` と $0$ を返します。
