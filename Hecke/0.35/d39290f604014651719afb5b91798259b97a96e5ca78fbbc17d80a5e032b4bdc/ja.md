```
minimum(m::T, I::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) where T <: Map{AbsSimpleNumField, AbsSimpleNumField} -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}
```

数体の埋め込み $m:k\to K$ と $K$ の整数理想が与えられたとき、交差 $I \cap \mathbf{Z}_k$ を求めます。
