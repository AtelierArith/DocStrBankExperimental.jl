```
ideal(A::AbstractAssociativeAlgebra, M::QQMatrix; M_in_hnf::Bool = false) -> AlgAssAbsOrdIdl
```

$$
A
$$

の理想を返し、基底行列は$M$です。`M_in_hnf == true`の場合、$M$がすでに下三角HNFであると仮定されます。
