```
 sysdiag = dsdiag(sys, k)
```

Build for a given descriptor system `sys` and non-negative integer `k` a descriptor system `sysdiag` obtained as `sysdiag = diag( sys, ..., sys )` (i.e., `k`-times repeated application of `append`).   
