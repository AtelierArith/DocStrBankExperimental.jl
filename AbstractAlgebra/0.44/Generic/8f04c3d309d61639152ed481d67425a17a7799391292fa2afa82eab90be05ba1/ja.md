```
gen(R::AbsPowerSeriesRing{T}) where T <: RingElement
```

冪級数環の生成元を返します。すなわち、$x + O(x^n)$ であり、ここで $n$ は冪級数環 $R$ の精度です。
