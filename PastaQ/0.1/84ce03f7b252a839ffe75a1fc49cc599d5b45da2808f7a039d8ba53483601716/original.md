```
qubits(n::Int)
```

Generate a $n$-qubit Hilbert space spanned by a basis $\{\sigma_j\}_{j=1}^n$. Each local degree of freedom is represented by an `ITensors.Index` object, which encode the local Hilbert space dimension and a unique identifier for automated tensor contractions.

```julia
q = qubits(3)
# 3-element Vector{ITensors.Index{Int64}}:
#  (dim=2|id=114|"Qubit,Site,n=1")
#  (dim=2|id=142|"Qubit,Site,n=2")
#  (dim=2|id=830|"Qubit,Site,n=3")
```
