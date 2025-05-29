```
ModuleIsomorphism(M1::FPModule{T}, M2::FPModule{T}, M::MatElem{T},
                  minv::MatElem{T}) where T <: RingElement
```

$$
M_1
$$

から$M_2$への写像$f$を行列$M$によって表現します。逆写像は自動的に計算されます。
