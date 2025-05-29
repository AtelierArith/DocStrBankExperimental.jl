```
remoterank2indices(remoteranks, indices::Tuple{Vararg{T1, N}}, rank2ghostindices::Dict{Int, Tuple{Vararg{T2, N}}}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{N, T1<:UnitRange, T2<:Union{UnitRange, Vector}}
```

get indices of ghost data in its hosting rank.
