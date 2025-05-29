```
ideal(A::AbstractAssociativeAlgebra, O::AlgAssRelOrd, M::PMat; side::Symbol = :nothing,
      M_in_hnf::Bool = false)
  -> AlgAssRelOrdIdl
```

$$
O
$$

の理想を$A$内で基底擬似行列$M$（$A$の基底において）で返します。理想が$O$の右/左/両側理想であることが知られている場合、`side`はそれぞれ`:right`/`:left`/`:twosided`に設定できます。`M_in_hnf == true`の場合、$M$はすでに下左擬似HNFにあると仮定されます。
