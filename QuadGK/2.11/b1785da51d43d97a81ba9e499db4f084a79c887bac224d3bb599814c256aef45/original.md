```
quadgk_segbuf(args...; kws...)
```

Identical to `quadgk(args...; kws...)`, but returns a tuple `(I, E, segbuf)` where `segbuf` is a segment buffer (storing the subintervals used for the final integral evaluation) that can be passed as a `segbuf` and/or `eval_segbuf` argument on subsequent calls to `quadgk` and related functions.
