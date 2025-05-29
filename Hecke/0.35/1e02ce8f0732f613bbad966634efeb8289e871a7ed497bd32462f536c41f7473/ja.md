```
simplify(x::FacElem{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, AbsNumFieldOrderIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> FacElem
simplify(x::FacElem{AbsSimpleNumFieldOrderFractionalIdeal, AbsNumFieldOrderFractionalIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> FacElem
```

`coprime_base`を使用して$x$の簡略化されたバージョンを取得します。つまり、簡略化されたバージョンではすべての基底理想が互いに素ですが、必ずしも素数であるとは限りません！
