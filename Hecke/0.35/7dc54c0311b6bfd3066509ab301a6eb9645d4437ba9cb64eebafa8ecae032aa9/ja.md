```
integral_model(E::EllipticCurve{T}) -> (F::EllipticCurve{T}, EllCrvIso, EllCrvIso)
  where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

与えられた楕円曲線 $E$ が QQ または数体 $K$ 上にある場合、$\mathcal{O}_K$ 上のモデルを持つ同型曲線 $F$ を返します。第二および第三の戻り値は、同型写像 $E \to F$ と $F \to E$ です。
