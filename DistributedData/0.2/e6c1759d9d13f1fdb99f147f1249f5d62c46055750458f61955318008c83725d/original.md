```
dexec(val, fn, workers)
```

Execute a function on workers, taking `val` as a parameter. Results are not collected. This is optimal for various side-effect-causing computations that are not easily expressible with `dtransform`.
