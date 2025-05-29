```
ptrace(a, indices)
```

Partial trace of the given basis, state or operator.

The `indices` argument, which can be a single integer or a vector of integers, specifies which subsystems are traced out. The number of indices has to be smaller than the number of subsystems, i.e. it is not allowed to perform a full trace.
