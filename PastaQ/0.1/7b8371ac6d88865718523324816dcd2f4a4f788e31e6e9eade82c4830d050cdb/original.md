```
productstate(hilbert::Vector{<:Index})
productstate(n::Int; dim = 2)
```

Generate an MPS wavefunction correponsponding to the product state

$|\psi\rangle = |0\rangle_1\otimes|0\rangle_2\otimes\dots|0\rangle_n$

It accepts both a Hilbert space or the number of modes and local dimension.
