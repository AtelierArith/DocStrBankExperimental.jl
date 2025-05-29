```
var_index(x::MPolyRingElem{T}) where {T <: RingElement}
```

Return the index of the given variable $x$. If $x$ is not a variable in a multivariate polynomial ring, an exception is raised.
