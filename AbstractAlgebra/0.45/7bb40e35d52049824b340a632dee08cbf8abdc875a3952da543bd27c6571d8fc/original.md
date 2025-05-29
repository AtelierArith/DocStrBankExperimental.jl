```
similar(x::MatRingElem, R::NCRing, n::Int)
similar(x::MatRingElem, R::NCRing)
similar(x::MatRingElem, n::Int)
similar(x::MatRingElem)
```

Create an uninitialized matrix ring element over the given ring and dimension, with defaults based upon the given source matrix ring element `x`.
