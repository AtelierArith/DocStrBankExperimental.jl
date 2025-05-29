```
print_connectivity(
    connectivity::LineConnectivity,
    ::Vector{Int} = Int[],
    io::IO = stdout
)
```

Prints the `connectivity` to `io`.

Qubits with their index in `path` are highlighted.

# Example

```jldoctest
julia> print_connectivity(LineConnectivity(3))
1──2──3

```
