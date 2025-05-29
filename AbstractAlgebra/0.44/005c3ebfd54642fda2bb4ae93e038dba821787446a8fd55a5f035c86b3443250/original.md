```
minpoly(M::MatElem{T}) where {T <: RingElement}
minpoly(S::PolyRing{T}, M::MatElem{T}) where {T <: RingElement}
```

Return the minimal polynomial $p$ of the square matrix $M$. If a polynomial ring $S$ over the same base ring as $Y$ is supplied, the resulting polynomial is an element of it.

# Examples

```jldoctest
julia> R = GF(13)
Finite field F_13

julia> S, y = polynomial_ring(R, :y)
(Univariate polynomial ring in y over R, y)

julia> M = R[7 6 1;
             7 7 5;
             8 12 5]
[7    6   1]
[7    7   5]
[8   12   5]

julia> A = minpoly(S, M)
y^2 + 10*y

julia> A = minpoly(M)
x^2 + 10*x

```
