```
divexact(x::AbsMSeries{T}, y::AbsMSeries{T}; check::Bool=true) where T <: RingElement
```

Return the exact quotient of the series $x$ by the series $y$. This function currently assumes $y$ is an invertible series.
