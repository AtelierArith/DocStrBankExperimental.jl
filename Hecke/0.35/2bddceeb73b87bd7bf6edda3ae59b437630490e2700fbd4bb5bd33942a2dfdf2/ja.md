```
is_integral_model(E::EllipticCurve{T}) -> Bool where T<:Union{QQFieldElem, AbsSimpleNumFieldElem}
```

与えられた楕円曲線 $E$ が QQ または数体 $K$ 上にある場合、$E$ が $E$ の整数モデルであれば true を返します。
