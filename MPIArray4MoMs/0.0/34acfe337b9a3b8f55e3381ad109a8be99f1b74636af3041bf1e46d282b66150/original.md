```
sync!(t::PatternTransfer{T, I}; comm = t.parent.comm, rank = t.parent.myrank, np = MPI.Comm_size(comm)) where{T, I}
```

同步 `t` 中的数据.
