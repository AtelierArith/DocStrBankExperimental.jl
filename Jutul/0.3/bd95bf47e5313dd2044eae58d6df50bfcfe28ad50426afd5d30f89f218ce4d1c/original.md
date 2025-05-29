```
LUSolver(; reuse_memory = true, check = true, max_size = 50000)
```

Direct solver that calls `lu` directly. Direct solvers are highly accurate, but are costly in terms of memory usage and execution speed for larger systems.
