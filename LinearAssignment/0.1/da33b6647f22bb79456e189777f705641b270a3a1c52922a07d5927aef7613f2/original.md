```
struct LAWorkspace{T}
    I::Vector{UInt32}       # assigned row indices for columns, cost[I[j], j]
    J::Vector{UInt32}       # assigned column indices for rows, cost[i, J[i]]
    u::Vector{T}            # dual row variables
    v::Vector{T}            # dual column variables
    d::Vector{T}            # shortest path lengths
    p::Vector{UInt32}       # predecessor array for shortest path tree
    sr::Vector{Bool}        # scanned rows
    sc::Vector{Bool}        # scanned columns
    free::Vector{UInt32}    # unassigned rows
    feasible::Ref{Bool}     # feasible assignment
end

LAWorkspace(cost::AbstractMatrix{T}) -> LAWorkspace{T}
LAWorkspace(::Type{T}, cost::AbstractMatrix) -> LAWorkspace{T}
LAWorkspace(::Type{T}, m::Integer, n::Integer) -> LAWorkspace{T}
```
