```
sync!(t::PatternTransfer{T, I}; comm = t.parent.comm, rank = t.parent.myrank, np = MPI.Comm_size(comm)) where{T, I}
```

`t` のデータを同期します。
