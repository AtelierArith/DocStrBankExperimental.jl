```
get_rank2ghostindices(ghostranks, indices, ghostindices; comm = MPI.COMM_WORLD, rank = MPI.Comm_rank(comm), np = MPI.Comm_size(comm))
```

ghostranks から ghostindices への辞書を取得します。
