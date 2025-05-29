```
prime_decomposition_nonindex(f::Map, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Z_K::AbsSimpleNumFieldOrder) -> Vector{Tuple{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, Int}}
```

数体 $k$ から $K$ への写像 $f: k\to K$ と $k$ の最大整域における素イデアルが与えられたとき、$K$ の最大整域における上にあるすべての素イデアルを見つけます。イデアルは $Z_K$ に属し、これはデフォルトで $K$ の「最大」整域を指します。
