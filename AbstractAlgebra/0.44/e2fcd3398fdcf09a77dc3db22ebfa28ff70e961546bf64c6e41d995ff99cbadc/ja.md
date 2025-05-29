```
resx(a::PolyRingElem{T}, b::PolyRingElem{T}) where T <: RingElement
```

タプル $(r, s, t)$ を返します。ここで $r$ は $a$ と $b$ の結果であり、$r = a\times s + b\times t$ となります。
