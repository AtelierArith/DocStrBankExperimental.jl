```
coeff(f::MPolyRingElem{T}, m::MPolyRingElem{T}) where T <: RingElement
```

多項式 $f$ の単項式 $m$ の係数を返します。該当する単項式がない場合は、ゼロが返されます。
