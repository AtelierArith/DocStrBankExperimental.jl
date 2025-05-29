```
nkd(code) -> Tuple{Int,Int,Union{Int,Missing}}
```

Return a descriptor in the format `(n, k, d)`, where `n` is the number of physical qubits, `k` is the number of logical qubits, and `d` is the distance of the code (or `missing` if unknown).

!!! note "Abstract method"
    This method should be implemented for concrete subtypes or duck-typed implementations of [`StabilizerCode`](@ref).

