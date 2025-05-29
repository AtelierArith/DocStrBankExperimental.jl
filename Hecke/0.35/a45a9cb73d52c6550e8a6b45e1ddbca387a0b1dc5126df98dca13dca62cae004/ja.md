```
ideal(A::AbstractAssociativeAlgebra, M::QQMatrix; M_in_hnf::Bool = false) -> AlgAssAbsOrdIdl
```

$$
A
$$

の基底行列$M$を持つイデアルを返します。`M_in_hnf == true`の場合、$M$がすでに左下HNFにあると仮定されます。
