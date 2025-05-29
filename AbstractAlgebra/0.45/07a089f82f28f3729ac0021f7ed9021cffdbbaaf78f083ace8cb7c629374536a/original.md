```
rank(M::MatrixElem{T}) where {T <: RingElement}
```

Return the rank of the matrix $M$.

# Examples

```jldoctest
julia> A = QQ[1 2; 3 4];

julia> d = rank(A)
2
```
