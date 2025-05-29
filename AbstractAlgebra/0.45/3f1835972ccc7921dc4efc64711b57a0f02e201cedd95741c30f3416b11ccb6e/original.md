```
to_univariate(R::PolyRing{T}, p::MPolyRingElem{T}) where T <: RingElement
```

Assuming the polynomial $p$ is actually a univariate polynomial, convert the polynomial to a univariate polynomial in the given univariate polynomial ring $R$. An exception is raised if the polynomial $p$ involves more than one variable.
