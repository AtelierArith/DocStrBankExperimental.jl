```
@unroll N expr
```

Takes a for loop as `expr` and informs the LLVM unroller to unroll it `N` times, if it is safe to do so.
