```
O(a::AbsPowerSeriesRingElem{T}) where T <: RingElement
```

$$
0 + O(x^\mathrm{deg}(a))
$$

を返します。通常、この関数は$x^n$をパラメータとして呼び出されます。すると、関数は冪級数$0 + O(x^n)$を返し、これは冪級数を構築する際にその精度を設定するために使用できます。
