```
learn_compose(;
    nvars, dom_size, param=nothing, icn=ICN(nvars, dom_size, param),
    X, X_sols, global_iter=100, local_iter=100, metric=hamming, popSize=200
)
```

Create an ICN, optimize it, and return its composition.
