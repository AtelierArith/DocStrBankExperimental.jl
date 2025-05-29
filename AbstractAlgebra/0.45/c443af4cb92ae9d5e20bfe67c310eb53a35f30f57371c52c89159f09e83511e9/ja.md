```
rref_rational(M::MatrixElem{T}) where {T <: RingElement}
```

行列 $M$ の階数 $r$ と $M$ の基底環における分母 $d$、および $A/d$ が $M$ の簡約行基本形であるような行列 $A$ からなるタプル $(r, A, d)$ を返します。分母は通常最小ではないことに注意してください。
