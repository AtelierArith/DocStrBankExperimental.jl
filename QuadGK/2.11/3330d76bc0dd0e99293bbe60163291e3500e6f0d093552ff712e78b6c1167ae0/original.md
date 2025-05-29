```
quadgk_segbuf_count(args...; kws...)
```

Identical to `quadgk_count(args...; kws...)`, but returns a tuple `(I, E, segbuf, count)` where `segbuf` is a segment buffer (storing the subintervals used for the final integral evaluation) that can be passed as a `segbuf` and/or `eval_segbuf` argument on subsequent calls to `quadgk` and related functions.
