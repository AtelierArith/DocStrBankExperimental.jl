```
to_bsf(
    pauli::Union{AbstractString,AbstractVector{<:AbstractString}}
) -> Union{BitVector,BitMatrix}
```

Convert the Pauli string operator(s) to binary symplectic form.

A single Pauli string is converted to a vector. A vector of Pauli strings is converted to a matrix where each row corresponds to a Pauli.

# Examples

```jldoctest
julia> to_bsf("XIZIY")
10-element BitVector:
 1
 0
 0
 0
 1
 0
 0
 1
 0
 1
```

```jldoctest
julia> to_bsf(["XIZIY", "IXZYI"])
2×10 BitMatrix:
 1  0  0  0  1  0  0  1  0  1
 0  1  0  1  0  0  0  1  1  0
```
