```
reversemap(f, args)
```

applies the function `f` to arguments `args` in reverse order and return the result. For now, the arguments `args` must be in the form of a simple tuple and the result is the tuple: `(f(args[end]),f(args[end-1]),...,f(args[1])`.

Also see: `map`, `ntuple`.
