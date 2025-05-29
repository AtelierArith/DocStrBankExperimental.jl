```
O(a::Generic.PuiseuxSeriesElem{T}) where T <: RingElement
```

Return $0 + O(x^\mathrm{val}(a))$. Usually this function is called with $x^n$ as parameter for some rational $n$. Then the function returns the Puiseux series $0 + O(x^n)$, which can be used to set the precision of a Puiseux series when constructing it.
