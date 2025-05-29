```
grank2ghostindices(ghostranks, ghostindices::Tuple{Vararg{T1, N}}, rank2indices::Dict{Int, Tuple{Vararg{T2, N}}}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{N, T1, T2}
grank2ghostindices(ghostranks, ghostindices::Tuple{Vararg{T1, N}}, rank2indices::Dict{Int, Tuple{Vararg{T2, N}}}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{N, T1<:Vector{Int}, T2}
grank2ghostindices(ghostranks, ghostindices::Tuple{Vararg{T1, N}}, rank2indices::Dict{Int, Tuple{Vararg{T2, N}}}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{N, T1<:Vector{UnitRange}, T2}
grank2ghostindices(ghostranks, ghostindices::NTuple{N, Union{UnitRange{Int}, Vector{Int}}}, rank2indices::Dict{Int, Tuple{Vararg{T2, N}}}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{N, T2}
```

get indices of ghost data in its hosting rank.
