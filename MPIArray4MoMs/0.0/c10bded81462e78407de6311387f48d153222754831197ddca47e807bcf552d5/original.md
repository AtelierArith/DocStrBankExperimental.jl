```
remoterank2indices(remoteranks, indices, rank2ghostindices::Dict{Int, T}; localrank = MPI.Comm_rank(MPI.COMM_WORLD)) where{T}
```

get remote rank and relative indices in data.
