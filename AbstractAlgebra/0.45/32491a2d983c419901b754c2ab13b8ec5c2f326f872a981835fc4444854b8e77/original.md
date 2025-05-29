```
swap_rows!(a::MatrixElem{T}, i::Int, j::Int) where T <: NCRingElement
```

Swap the $i$th and $j$th row of $a$ in place. The function returns the mutated matrix (since matrices are assumed to be mutable in AbstractAlgebra.jl).

# Examples

```jldoctest
julia> M = identity_matrix(ZZ, 3)
[1   0   0]
[0   1   0]
[0   0   1]

julia> swap_rows!(M, 1, 2)
[0   1   0]
[1   0   0]
[0   0   1]

julia> M  # was modified
[0   1   0]
[1   0   0]
[0   0   1]
```
