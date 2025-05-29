```
ModuleIsomorphism(M1::FPModule{T}, M2::FPModule{T}, M::MatElem{T},
                  minv::MatElem{T}) where T <: RingElement
```

$$
M_1 \to M_2
$$

を行列$M$で表される同型$f$を作成します。逆写像は自動的に計算されます。
