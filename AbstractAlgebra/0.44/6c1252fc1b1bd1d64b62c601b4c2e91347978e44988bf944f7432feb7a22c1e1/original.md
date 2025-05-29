```
div(f::T, g::T) where T <: RingElem
```

Return the Euclidean quotient of $f$ by $g$. A `DivideError` should be thrown if $g$ is zero.
