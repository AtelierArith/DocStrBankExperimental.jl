```
regulator(x::Vector{T}, abs_tol::Int = 64) -> ArbFieldElem
```

Compute the regulator $r$ of the elements in $x$, such that the radius of $r$ is less then `-2^abs_tol`.
