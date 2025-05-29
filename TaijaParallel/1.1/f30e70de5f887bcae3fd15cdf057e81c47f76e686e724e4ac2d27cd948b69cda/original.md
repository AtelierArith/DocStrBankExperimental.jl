```
@with_parallelizer(parallelizer, expr)
```

This macro can be used to parallelize a function call or block of code. The macro will check that the function is parallelizable and then call `parallelize` with the supplied `parallelizer` and `expr`.
