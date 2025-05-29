```
get_rank2ghostindices(ghostranks, indices, ghostindices; comm = MPI.COMM_WORLD, rank = MPI.Comm_rank(comm), np = MPI.Comm_size(comm))
```

获取 ghostranks 到 ghostindices 的字典。
