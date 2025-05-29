```
get_adjacency_list(connectivity::AbstractConnectivity)::Dict{Int,Vector{Int}}
```

Given an object of type `AbstractConnectivity`, `get_adjacency_list` returns a `Dict` where each key is a qubit index. Every dictionary value is a `Vector` that lists all the qubits which are adjacent on the connectivity to the qubit key. Positions in `connectivity.excluded_positions` are not included as keys nor values.

# Example

```jldoctest
julia> connectivity = LineConnectivity(6)
LineConnectivity{6}
1──2──3──4──5──6


julia> get_adjacency_list(connectivity)
Dict{Int64, Vector{Int64}} with 6 entries:
  5 => [4, 6]
  4 => [3, 5]
  6 => [5]
  2 => [1, 3]
  3 => [2, 4]
  1 => [2]

julia> connectivity = LatticeConnectivity(3, 4)
LatticeConnectivity{3,4}
        1 
        | 
  9 ──  5 ──  2 
        |     | 
       10 ──  6 ──  3 
              |     | 
             11 ──  7 ──  4 
                    |     | 
                   12 ──  8 
  
julia> get_adjacency_list(connectivity)
Dict{Int64, Vector{Int64}} with 12 entries:
  5  => [1, 10, 9, 2]
  12 => [7, 8]
  8  => [4, 12]
  1  => [5]
  6  => [2, 11, 10, 3]
  11 => [6, 7]
  9  => [5]
  3  => [7, 6]
  7  => [3, 12, 11, 4]
  4  => [8, 7]
  2  => [6, 5]
  10 => [5, 6]

```

!!! note
    The `get_adjacency_list` function cannot be used for `AllToAllConnectivity` since this type of connectivity places no upper bound on the number of qubits and all qubits connect to each other by definition. A finite list of adjacent qubits thus cannot be constructed.

