```
coeff(f::MPolyRingElem{T}, m::MPolyRingElem{T}) where T <: RingElement
```

多項式 $f$ の単項式 $m$ の係数を返します。そのような単項式が存在しない場合は、ゼロが返されます。
