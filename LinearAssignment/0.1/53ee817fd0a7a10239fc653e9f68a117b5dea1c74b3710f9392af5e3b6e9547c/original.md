```
struct LAWorkspaceCSC{Tv}
    I::Vector{UInt32}           # assigned row indices for columns, cost[I[j], j]
    J::Vector{UInt32}           # assigned column indices for rows, cost[i, J[i]]
    u::Vector{Tv}               # dual row variables
    v::Vector{Tv}               # dual column variables
    d::Vector{Tv}               # shortest path lengths
    p::Vector{UInt32}           # predecessor array for shortest path tree
    srv::Vector{Bool}           # scanned rows visited
    sri::Vector{UInt32}         # scanned rows indices
    scv::Vector{Bool}           # scanned cols visited
    sci::Vector{UInt32}         # scanned cols indices
    sdv::Vector{Bool}           # set path lengths visited
    sdi::Vector{UInt32}         # set path lengths indices
    qdi::Vector{UInt32}         # set path lengths indices not scanned
    qdj::Vector{UInt32}         # set path lengths indices not scanned reverse
    feasible::RefValue{Bool}    # feasible assignment
end

LAWorkspaceCSC(cost::SparseMatrixCSC{Tv}) -> LAWorkspaceCSC{Tv}
LAWorkspaceCSC(::Type{Tv}, cost::SparseMatrixCSC) -> LAWorkspaceCSC{Tv}
LAWorkspaceCSC(::Type{Tv}, m::Integer, n::Integer) -> LAWorkspaceCSC{Tv}
```
