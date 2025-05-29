```
to_pauli(bsf::AbstractVecOrMat{Bool}) -> Union{String,Vector{String}}
```

Convert the binary symplectic form to Pauli string operator(s).

A vector is converted to a single Pauli string. A matrix is converted row-by-row to a collection of Pauli strings.

# Examples

```jldoctest
julia> to_pauli(BitVector([1, 0, 0, 0, 1, 0, 0, 1, 0, 1]))
"XIZIY"
```

```jldoctest
julia> to_pauli(BitMatrix([1 0 0 0 1 0 0 1 0 1; 0 1 0 1 0 0 0 1 1 0]))
2-element Vector{String}:
 "XIZIY"
 "IXZYI"
```
