```
sync!(t::ArrayTransfer; comm = t.parent.comm, rank = t.parent.myrank, np = MPI.Comm_size(comm))
```

t内のデータを同期します。
