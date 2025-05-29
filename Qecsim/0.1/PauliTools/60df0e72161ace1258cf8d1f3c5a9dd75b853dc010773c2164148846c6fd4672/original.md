```
weight(pauli::Union{AbstractString,AbstractVector{<:AbstractString}}) -> Int
```

Return the weight of the Pauli string operator(s).

# Examples

```jldoctest
julia> weight("XIZIY")
3
```

```jldoctest
julia> weight(["XIZIY", "XXXXX"])
8
```
