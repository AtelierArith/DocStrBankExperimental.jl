```
is_isomorphic(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldElem
is_isomorphic(I::NfFracOrdIdl, J::NfFracOrdIdl) -> Bool, AbsSimpleNumFieldElem
is_isomorphic(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl) -> Bool, AbstractAssociativeAlgebraElem
```

与えられた二つの（分数）イデアル $I$ と $J$ は、$Q$-étale 代数 $A$ のオーダー $R$ のものであり、この関数は、$I = aJ$ となるような要素 $a \in A$ が存在すれば `true` を返し、そうでなければ `false` を返します。
