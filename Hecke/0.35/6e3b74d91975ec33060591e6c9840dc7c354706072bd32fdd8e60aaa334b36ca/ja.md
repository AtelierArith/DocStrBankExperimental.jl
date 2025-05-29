```
ideal(A::AbstractAssociativeAlgebra, O::AlgAssRelOrd, M::PMat; side::Symbol = :nothing,
      M_in_hnf::Bool = false)
  -> AlgAssRelOrdIdl
```

$$
O
$$

の$A$におけるイデアルを、基底擬似行列$M$（$A$の基底において）で返します。イデアルが$O$の右/左/両側イデアルであることが知られている場合、`side`をそれぞれ`:right`/`:left`/`:twosided`に設定できます。`M_in_hnf == true`の場合、$M$はすでに下左擬似HNFにあると仮定されます。
