```
diagonal_matrix(x::T...) where T <: NCRingElement -> MatElem{T}
diagonal_matrix(x::Vector{T}) where T <: NCRingElement -> MatElem{T}
diagonal_matrix(R::NCRing, x::Vector{T}) where T <: NCRingElement -> MatElem{T}
```

Returns a diagonal matrix whose diagonal entries are the elements of $x$. If a ring $R$ is given then it is used a parent for the entries of the created matrix. Otherwise the parent is inferred from the vector $x$.

# Examples

```jldoctest
julia> diagonal_matrix(ZZ(1), ZZ(2))
[1   0]
[0   2]

julia> diagonal_matrix([ZZ(3), ZZ(4)])
[3   0]
[0   4]

julia> diagonal_matrix(ZZ, [5, 6])
[5   0]
[0   6]
```
