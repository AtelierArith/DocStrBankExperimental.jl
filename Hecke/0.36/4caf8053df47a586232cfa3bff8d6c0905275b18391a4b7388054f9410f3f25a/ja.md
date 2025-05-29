```
ideal(A::AbstractAssociativeAlgebra, O::AlgAssAbsOrd, M::QQMatrix; side::Symbol = :nothing,
      M_in_hnf::Bool = false)
  -> AlgAssAbsOrdIdl
```

$$
O
$$

の$A$におけるイデアルを、基底行列$M$（$A$の基底において）で返します。イデアルが$O$の右/左/両側イデアルであることが知られている場合、`side`をそれぞれ`:right`/`:left`/`:twosided`に設定できます。`M_in_hnf == true`の場合、$M$はすでに下三角HNFにあると仮定されます。
