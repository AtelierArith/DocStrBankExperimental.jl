```
path_search(
    origin::Int,
    target::Int,
    connectivity::AbstractConnectivity,
    excluded::Vector{Int} = Vector{Int}([])
)::Vector{Int}
```

Find the shortest path between origin and target qubits in terms of  Manhattan distance. The path is found for any `connectivity::AbstractConnectivity` using the Breadth-first search algorithm. Positions that are specified in the  `excluded` optional argument are avoided. If no path exists, returns an empty `Vector{Int}`.

# Example

```jldoctest
julia> connectivity = LineConnectivity(6)
LineConnectivity{6}
1──2──3──4──5──6


julia> path = path_search(2, 5, connectivity)
4-element Vector{Int64}:
 5
 4
 3
 2

```

For [`LatticeConnectivity`](@ref), the [`print_connectivity()`](@ref) method is used to visualize the path. The qubits along the path between origin and target are marked with `( )`

```jldoctest; output=false
julia> connectivity = LatticeConnectivity(6, 4)
LatticeConnectivity{6,4}
              1 
              | 
        9 ──  5 ──  2 
        |     |     | 
 17 ── 13 ── 10 ──  6 ──  3 
  |     |     |     |     | 
 21 ── 18 ── 14 ── 11 ──  7 ──  4 
        |     |     |     |     | 
       22 ── 19 ── 15 ── 12 ──  8 
              |     |     | 
             23 ── 20 ── 16 
                    | 
                   24 


julia> path = path_search(3, 24, connectivity)
6-element Vector{Int64}:
 24
 20
 16
 12
  7
  3

```
