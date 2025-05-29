```
prime_decomposition_nonindex(f::Map, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Z_K::AbsSimpleNumFieldOrder) -> Vector{Tuple{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}}
```

数体 $k$ から $K$ への写像 $f: k\to K$ と $\mathbb Q$ 上で定義された最大整域の素イデアルを考え、$K$ の最大整域の上にあるすべての素イデアルを見つけます。イデアルは $Z_K$ に属し、これはデフォルトで $K$ の「最大」整域を指します。
