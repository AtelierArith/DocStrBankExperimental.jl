```
O(a::RelPowerSeriesRingElem{T}) where T <: RingElement
```

Return $0 + O(x^\mathrm{deg}(a))$. Usually this function is called with $x^n$ as parameter. Then the function returns the power series $0 + O(x^n)$, which can be used to set the precision of a power series when constructing it.
