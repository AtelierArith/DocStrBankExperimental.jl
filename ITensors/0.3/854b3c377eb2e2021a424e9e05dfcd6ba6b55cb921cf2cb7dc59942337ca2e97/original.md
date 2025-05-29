```
op(opname::String,sites::Vector{<:Index},n::Int; kwargs...)
```

Return an ITensor corresponding to the operator named `opname` for the n'th Index in the array `sites`.

# Example

```julia
s = siteinds("S=1/2", 4)
Sz2 = op("Sz", s, 2)
```
