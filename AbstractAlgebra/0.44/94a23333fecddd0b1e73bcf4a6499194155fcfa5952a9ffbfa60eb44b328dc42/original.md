```
swap_cols!(a::MatrixElem{T}, i::Int, j::Int) where T <: NCRingElement
```

Swap the $i$th and $j$th column of $a$ in place. The function returns the mutated matrix (since matrices are assumed to be mutable in AbstractAlgebra.jl).
