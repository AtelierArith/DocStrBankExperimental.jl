```
norm(m::T, I::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) where T <: Map{AbsSimpleNumField, AbsSimpleNumField} -> AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}
```

数体の埋め込み $m:k\to K$ と $K$ の整数理想が与えられたとき、ノルム $N_{K/k}(I)$ を求めます。
