```
ModuleIsomorphism(M1::FPModule{T}, M2::FPModule{T}, M::MatElem{T},
                  minv::MatElem{T}) where T <: RingElement
```

Create the isomorphism $f : M_1 \to M_2$ represented by the matrix $M$. The inverse morphism is automatically computed.
