```
O(a::Generic.PuiseuxSeriesElem{T}) where T <: RingElement
```

$$
0 + O(x^\mathrm{val}(a))
$$

を返します。通常、この関数はいくつかの有理数 $n$ のパラメータとして $x^n$ と共に呼び出されます。すると、この関数は Puiseux シリーズ $0 + O(x^n)$ を返し、これを使用して構築時に Puiseux シリーズの精度を設定できます。
