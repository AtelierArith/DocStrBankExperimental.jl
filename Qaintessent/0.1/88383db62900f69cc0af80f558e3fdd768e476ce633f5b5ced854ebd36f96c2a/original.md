```
num_wires(::AbstractGate)
```

returns number of wires affected by AbstractGate object.

# Examples

```jldoctest
julia> num_wires(X)
1

julia> num_wires(SwapGate())
2
```
