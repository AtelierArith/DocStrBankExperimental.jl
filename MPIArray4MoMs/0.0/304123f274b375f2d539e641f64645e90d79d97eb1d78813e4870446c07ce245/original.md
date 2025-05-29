```
sync!(t::ArrayTransfer; comm = t.parent.comm, rank = t.parent.myrank, np = MPI.Comm_size(comm))
```

sync data in t.
