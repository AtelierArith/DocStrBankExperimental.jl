```
relative_degree(A::Matrix{<:Integer}, u::Integer, V::Vector{<:Integer}) :: Int32
```

Compute the number of edges going from `u` into any vertex in the subset of points `V`.

# Arguments

-`A::Matrix{<:Integer}`: the adjacency matrix. `A[i,j] = 1` if there is an edge going from `i` to `j`
