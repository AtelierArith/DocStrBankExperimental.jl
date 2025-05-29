```
is_locally_isomorphic(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal) -> Bool
is_locally_isomorphic(I::NfFracOrdIdl, J::NfFracOrdIdl) -> Bool
is_locally_isomorphic(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl) -> Bool
```

与えられた二つの（分数）イデアル $I$ と $J$ は、$Q$-étale 代数のオーダー $R$ のものであり、この関数は $I_p$ と $J_p$ が $R$ のすべての素数 $p$ に対して同型であれば `true` を返し、そうでなければ `false` を返します。
