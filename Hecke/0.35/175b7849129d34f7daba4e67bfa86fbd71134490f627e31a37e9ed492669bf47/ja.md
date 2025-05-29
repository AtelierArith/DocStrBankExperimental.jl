```
norm(m::T, a::AbsSimpleNumFieldElem) where T <: Map{AbsSimpleNumField, AbsSimpleNumField} -> AbsSimpleNumFieldElem
```

数体の埋め込み $m:k\to K$ と $K$ の要素 $a$ が与えられたとき、ノルム $N_{K/k}(a)$ を求めます。
