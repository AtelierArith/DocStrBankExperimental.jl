```
step!(ch::AbstractChain)
```

Take a single step in the chain, returning the next sample. The return type depends on AbstractChain subtype. The only change in the chain `ch` is the iterator state; the samples are unchanged.
