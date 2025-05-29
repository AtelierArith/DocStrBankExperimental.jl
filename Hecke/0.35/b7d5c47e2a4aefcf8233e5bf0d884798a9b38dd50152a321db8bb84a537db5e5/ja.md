```
ideal(A::AbstractAssociativeAlgebra, M::PMat; M_in_hnf::Bool = false) -> AlgAssRelOrdIdl
```

$$
A
$$

の基底擬似行列$M$を持つイデアルを返します。`M_in_hnf == true`の場合、$M$はすでに左下擬似HNFにあると仮定されます。
