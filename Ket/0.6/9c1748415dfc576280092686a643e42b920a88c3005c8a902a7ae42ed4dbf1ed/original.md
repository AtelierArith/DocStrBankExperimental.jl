```
pauli([T=ComplexF64,], ind::Vector{<:Integer})
```

Constructs the Pauli matrices: 0 or "I" for the identity, 1 or "X" for the Pauli X operation, 2 or "Y" for the Pauli Y operator, and 3 or "Z" for the Pauli Z operator. Vectors of integers between 0 and 3 or strings of I, X, Y, Z automatically generate Kronecker products of the corresponding operators.
