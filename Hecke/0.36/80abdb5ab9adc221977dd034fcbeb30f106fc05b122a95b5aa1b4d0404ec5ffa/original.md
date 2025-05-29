```
minkowski_map(a::AbsSimpleNumFieldElem, abs_tol::Int) -> Vector{ArbFieldElem}
```

Returns the image of $a$ under the Minkowski embedding. Every entry of the array returned is of type `ArbFieldElem` with radius less then `2^(-abs_tol)`.
