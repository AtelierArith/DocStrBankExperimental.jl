```
isless(a::MPoly{T}, b::MPoly{T}) where {T <: RingElement}
```

Return `true` if the monomial $a$ is less than the monomial $b$ with respect to the monomial ordering of the parent ring.
