```
print_connectivity(
    connectivity::LatticeConnectivity,
    path::Vector{Int} = Vector{Int}(),
    io::IO = stdout,
)
```

Prints the `connectivity` to `io`.

Qubits with their index in `path` are highlighted.

# Example

```jldoctest
julia> connectivity=LatticeConnectivity(3,3);

julia> path = path_search(1, 3, connectivity);

julia> print_connectivity(connectivity, path)
     (1)
      | 
 7 ──(4)── 2 
      |    | 
     (8)──(5)──(3)
           |    | 
           9 ── 6 

```
