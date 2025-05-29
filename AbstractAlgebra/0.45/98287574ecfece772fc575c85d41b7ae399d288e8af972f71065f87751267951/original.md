```
divrem(f::T, g::T) where T <: RingElem
```

Return a pair `q, r` consisting of the Euclidean quotient and remainder of $f$ by $g$. A `DivideError` should be thrown if $g$ is zero.
