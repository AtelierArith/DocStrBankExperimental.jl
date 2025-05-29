```
is_locally_isomorphic(I::AbsNumFieldOrderIdeal, J::AbsNumFieldOrderIdeal) -> Bool
is_locally_isomorphic(I::NfFracOrdIdl, J::NfFracOrdIdl) -> Bool
is_locally_isomorphic(I::AlgAssAbsOrdIdl, J::AlgAssAbsOrdIdl) -> Bool
```

Given two (fractional) ideals $I$ and $J$ of an order $R$ of an $Q$-étale algebra, this function returns `true` if $I_p$ and $J_p$ are isomorphic for all primes $p$ of $R$ and `false` otherwise.
