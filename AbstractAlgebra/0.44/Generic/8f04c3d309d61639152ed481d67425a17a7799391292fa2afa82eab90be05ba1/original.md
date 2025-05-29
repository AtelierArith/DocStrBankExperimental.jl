```
gen(R::AbsPowerSeriesRing{T}) where T <: RingElement
```

Return the generator of the power series ring, i.e. $x + O(x^n)$ where $n$ is the precision of the power series ring $R$.
