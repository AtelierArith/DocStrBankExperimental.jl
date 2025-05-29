```
integral_model(E::EllipticCurve{T}) -> (F::EllipticCurve{T}, EllCrvIso, EllCrvIso)
  where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

Given an elliptic curve $E$ over QQ or a number field $K$, returns an isomorphic curve $F$ with model over $\mathcal{O}_K$. The second and third return values are the isomorpisms $E \to F$ and $F \to E$.
